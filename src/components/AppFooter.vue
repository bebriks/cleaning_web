<template>
  <v-footer
    class="footer"
    color="rgba(106, 186, 162, 1)"
    height="auto"
  >
    <v-container>
      <div class="footer-content">
        <h1 class="footer-title">Наши контакты</h1>

        <div class="contacts-container justify-center">
          <div class="phone-block">
            <p class="phone-text">+7 922 197-71-32</p>
            <PhoneIcon class="phone-icon" />
            <a class="whatsapp-link" href="whatsapp://send?phone=+79221977132">
              <v-icon>mdi-whatsapp</v-icon>
              Есть WhatsApp
            </a>
          </div>

          <!-- <div class="social-icons">
            <a class="social-icon" href="#">
              <v-icon>mdi-vk</v-icon>
            </a>
            <a class="social-icon" href="#">
              <v-icon>mdi-telegram</v-icon>
            </a>
            <a class="social-icon" href="#">
              <v-icon>mdi-instagram</v-icon>
            </a>
          </div> -->
        </div>
      </div>
    </v-container>
  </v-footer>
</template>

<script setup lang="ts">
  import PhoneIcon from './icons/Phone.vue'
</script>

<style scoped lang="sass">
.footer
  padding: 40px 0 !important

.footer-content
  display: flex
  flex-direction: column
  align-items: center
  text-align: center

.footer-title
  font-weight: 300
  font-size: 36px
  margin-bottom: 30px

.contacts-container
  display: flex
  flex-direction: column
  gap: 25px
  width: 100%
  max-width: 500px

.phone-block
  display: flex
  align-items: center
  justify-content: center
  gap: 15px
  background: rgba(255, 255, 255, 0.2)
  border-radius: 12px
  padding: 15px
  backdrop-filter: blur(5px)

.phone-icon
  flex-shrink: 0

.phone-text
  text-align: left
  font-size: 18px
  font-weight: 400

.whatsapp-link
  display: flex
  align-items: center
  gap: 5px
  color: #25D366 !important
  text-decoration: none
  font-weight: 500
  transition: opacity 0.3s
  &:hover
    opacity: 0.8
    text-decoration: underline

.social-icons
  display: flex
  justify-content: center
  gap: 20px

.social-icon
  display: flex
  align-items: center
  justify-content: center
  width: 50px
  height: 50px
  background: rgba(255, 255, 255, 0.2)
  border-radius: 50%
  transition: all 0.3s ease
  .v-icon
    color: white
    font-size: 24px
  &:hover
    background: rgba(255, 255, 255, 0.3)
    transform: translateY(-3px)

/* Адаптивность */
@media (max-width: 600px)
  .footer-title
    font-size: 24px

  .phone-block
    flex-direction: column
    text-align: center

  .phone-text
    text-align: center

  .whatsapp-link
    justify-content: center

@media (min-width: 960px)
  .contacts-container
    flex-direction: row
    justify-content: space-between
    align-items: center
</style>
