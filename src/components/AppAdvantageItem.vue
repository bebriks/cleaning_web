<script setup lang="ts">
  import type { DefineComponent } from 'vue'
  import Medal from './icons/Medal.vue'
  import Money from './icons/Money.vue'
  import Shield from './icons/Shield.vue'

  type VueComponent = DefineComponent<{}, {}, any, {}, {}, any, any, any>

  type IconMap = Record<string, VueComponent> & {
    Money: VueComponent
    Shield: VueComponent
    Medal: VueComponent
  }

  const iconMap: IconMap = {
    Money: Money as VueComponent,
    Shield: Shield as VueComponent,
    Medal: Medal as VueComponent,
  }

  interface AdvantageItem {
    title: string
    icon: keyof typeof iconMap
    cardText: string
    elements: string[]
  }

  const items: AdvantageItem[] = [
    {
      title: 'Без доплат и переплат',
      icon: 'Money',
      cardText: 'Оплата по факту выполнения работы',
      elements: ['Квартира', 'Дом', 'Коттедж', 'Офис', 'Складские помещения'],
    },
    {
      title: 'Превосходный результат',
      icon: 'Medal',
      cardText: 'Возможна химчистка и мойка окон',
      elements: ['Химчистка', 'Мойка окон', 'Баннеры и реклама'],
    },
    {
      title: 'Используем гипоаллергенные средства',
      icon: 'Shield',
      cardText: 'Наши средства подбираются для каждой поверхности по типу',
      elements: ['После ремонта', 'Антибактериальная', 'На постоянной основе', 'Генеральная', 'Срочная'],
    },
  ]
</script>

<template>
  <v-container id="services">
    <h2 class="section-title" data-aos="fade-up">Услуги</h2>
    <v-row class="advantage-columns" justify="space-around">
      <v-col
        v-for="(item, index) in items"
        :key="item.title"
        class="d-flex justify-center"
        cols="12"
        sm="4"
      >
        <div
          class="advantage-column"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <div class="advantage-item">
            <component :is="iconMap[item.icon]" />
            <span class="title">{{ item.title }}</span>
          </div>

          <v-card
            class="advantage-card"
            variant="flat"
          >
            <v-card-text class="advantage-card__text">
              {{ item.cardText }}
            </v-card-text>
          </v-card>

          <div class="advantage-list">
            <ul class="list">
              <li v-for="element in item.elements" :key="element" :title="element">
                {{ element }}
              </li>
            </ul>
          </div>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="sass">
.title
  font-size: 20px
  font-weight: 500
  margin-top: 10px

.advantage-columns
  margin-bottom: 100px

.advantage-column
  display: flex
  flex-direction: column
  align-items: center
  max-width: 300px
  width: 100%
  gap: 20px

.advantage-item
  display: flex
  flex-flow: column
  align-items: center
  gap: 8px
  width: 100%
  text-align: center
  transition: transform 0.3s ease
  height: 137px
  &:hover
    transform: translateY(-5px)
.section-title
  text-align: center
  font-size: 2.5rem
  margin-bottom: 60px
  color: rgba(106, 186, 162, 1)
  position: relative
  padding-top: 80px
  &::after
    content: ''
    position: absolute
    bottom: -15px
    left: 50%
    transform: translateX(-50%)
    width: 80px
    height: 4px
    background: rgba(106, 186, 162, 1)
    border-radius: 2px

.advantage-card
  width: 100%
  text-align: center
  align-content: center
  height: 150px
  transition: all 0.3s ease
  .advantage-card__text
    font-size: 20px
  &:hover
    box-shadow: 0 10px 20px rgba(0,0,0,0.1), 0 6px 6px rgba(0,0,0,0.1)
    transform: translateY(-3px)

.v-card-text
  padding: 18px 15px !important
  font-size: 16px
  font-weight: 400
  line-height: 1.5

.advantage-list
  width: 100%

.list
  list-style: none
  padding-left: 0
  margin-top: 40px
  li
    position: relative
    padding-left: 30px
    margin-bottom: 15px
    font-size: 20px
    line-height: 1.6
    &::before
      content: ''
      position: absolute
      left: 0
      top: 50%
      transform: translateY(-50%)
      width: 15px
      height: 15px
      background-color: rgba(126, 190, 170, 1)
      border-radius: 50%
      transition: transform 0.3s ease
    &:hover::before
      transform: translateY(-50%) scale(1.1)

// Адаптивность для мобильных
@media (max-width: 768px)
  .advantage-column
    max-width: 100%
    margin-bottom: 40px
    &:last-child
      margin-bottom: 0
</style>
