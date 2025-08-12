<template>
  <div id="main" class="main-hero">
    <div class="hero-content" data-aos="fade-up" data-aos-duration="1000">
      <h2 class="hero-title">
        Клининговые услуги
        <br>
        в
        <br>
        Екатеринбурге
      </h2>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.main-hero {
  position: relative;
  width: 100vw;
  min-height: 100vh;
  background:
    linear-gradient(rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)),
    url("@/images/main.jpg") center/cover no-repeat;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding: 0 5%;
  margin-top: 63px;
}

.hero-content {
  background: rgba(217, 217, 217, 0.8);
  border-radius: 8px;
  padding: 20px;
  text-align: center;
  backdrop-filter: blur(5px);
}

.hero-title {
  font-weight: 300;
  line-height: 1.4;
  margin: 0;
  color: #333;
  font-size: 48px;
}

@media (max-width: 768px) {
  .main-hero {
    justify-content: center;
    padding: 20px;
  }
  .hero-content {
    max-width: 100%;
  }
}
</style>
