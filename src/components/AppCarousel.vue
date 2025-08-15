<script setup lang="ts">
  import image13 from '@/images/image_13.jpg'
  import image14 from '@/images/image_14.jpg'
  import image15 from '@/images/image_15.jpg'
  import image16 from '@/images/image_16.jpg'
  import image17 from '@/images/image_17.jpg'
  import image18 from '@/images/image_18.jpg'
  import image19 from '@/images/image_19.jpg'
  import image20 from '@/images/image_20.jpg'
  import image21 from '@/images/image_21.jpg'
  import image22 from '@/images/image_22.jpg'

  const workCategories = [
    {
      title: 'Уборка после ремонта',
      items: [
        { src: image13 },
        { src: image14 },
      ],
    },
    {
      title: 'Детский садик после ремонта',
      items: [
        { src: image15 },
        { src: image16 },
      ],
    },
    {
      title: 'Химчистка коврового покрытия',
      items: [
        { src: image19 },
        { src: image20 },
      ],
    },
    {
      title: 'Уборка после ремонта',
      items: [
        { src: image21 },
        { src: image22 },
      ],
    },
    {
      title: 'Коттедж после ремонта',
      items: [
        { src: image18 },
      ],
    },
    {
      title: 'Химчистка дивана',
      items: [
        { src: image17 },
      ],
    },
  ]
</script>

<template>
  <section id="works" class="works-section" itemscope itemtype="https://schema.org/ImageGallery">
    <v-container>
      <h1 class="section-title" data-aos="fade-up" itemprop="headline">Наши работы</h1>

      <div class="work-categories">
        <article
          v-for="(category, index) in workCategories"
          :key="index"
          class="work-category"
          :class="{ 'reverse': index % 2 !== 0 }"
          itemprop="hasPart"
          itemscope
          itemtype="https://schema.org/ImageObject"
        >
          <h2 class="category-title" data-aos="fade-right" itemprop="name">
            {{ category.title }}
          </h2>

          <div class="carousel-container" data-aos="fade-up">
            <v-carousel
              class="work-carousel"
              height="400"
              hide-delimiters
              :show-arrows="category.items.length > 1"
            >
              <v-carousel-item
                v-for="(item, i) in category.items"
                :key="i"
              >
                <div class="carousel-image-container">
                  <img
                    :alt="item.src"
                    class="carousel-image"
                    itemprop="contentUrl"
                    loading="lazy"
                    :src="item.src"
                  >
                </div>
                <div class="carousel-overlay" />
              </v-carousel-item>
            </v-carousel>
          </div>
        </article>
      </div>
    </v-container>
  </section>
</template>

<style scoped lang="sass">
@use '../styles/settings';
.works-section
  padding: 80px 0
  background-color: #FFFFFF

.section-title
  text-align: center
  font-size: 2.5rem
  margin-bottom: 60px
  color: rgba(106, 186, 162, 1)
  position: relative

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

.work-categories
  display: flex
  flex-direction: column
  gap: 60px

.category-title
  font-size: 1.8rem
  color: rgba(106, 186, 162, 1)
  margin-bottom: 20px
  padding-left: 15px
  border-left: 4px solid rgba(106, 186, 162, 1)

.work-category
  display: flex
  flex-direction: row
  justify-content: space-around
  gap: 30px

  &.reverse
    flex-direction: row-reverse
    z-index: 3
    .category-title
      border: none
      padding-left: 0
      border-right: 4px solid rgba(106, 186, 162, 1)
      padding-right: 15px

.carousel-container
  width: 100%
  max-width: 800px

.carousel-image-container
  width: 100%
  height: 100%
  position: relative

.carousel-image
  width: 100%
  height: 100%
  object-fit: fill
  display: block

.work-carousel
  border-radius: 12px
  overflow: hidden
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1)

  &:hover
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15)
.carousel-overlay
  position: absolute
  bottom: 0
  left: 0
  right: 0
  height: 40%
  background: linear-gradient(transparent, rgba(0, 0, 0, 0.5))

@media (max-width: 960px)
  .works-section
    padding: 60px 0

  .section-title
    font-size: 2rem
    margin-bottom: 40px

  .work-category
    gap: 20px

  .category-title
    font-size: 1.5rem
    text-align: center
    padding-left: 0
    border-left: 3px solid rgba(106, 186, 162, 1)
    padding-bottom: 10px

@media (max-width: 600px)
  .works-section
    padding: 40px 0

  .section-title
    font-size: 1.8rem

  .category-title
    font-size: 1.3rem

  .work-carousel
    height: 300px
</style>
