<template>
  <div class="bili-header__banner">
    <picture class="banner-img">
      <img :src="iconLogoImg" alt="" />
    </picture>
    <div class="animated-banner">
      <video
        v-if="randomBanner"
        :src="randomBanner"
        autoplay
        muted
        loop
        playsinline
        class="banner-video"
      />
    </div>
    <div class="banner-inner">
      <a href="/" class="banner-logo">
        <img
          :src="textLogoImg"
          alt="bilibili"
          class="banner-logo-img"
        />
      </a>
    </div>
    <div class="taper-line"></div>
  </div>
</template>

<script setup lang="ts">
import iconLogoImg from '~/assets/images/header/bili_icon_logo_light.svg';
import textLogoImg from '~/assets/images/header/bili_text_logo.png';

const bannerVideos = [
  '/videos/banner/bili_2021_summer_day_clear.webm',
  '/videos/banner/bili_2021_summer_day_rainy.webm',
  '/videos/banner/bili_2021_summer_day_windy.webm',
  '/videos/banner/bili_2021_summer_evening_clear.webm',
  '/videos/banner/bili_2021_summer_evening_rainy.webm',
  '/videos/banner/bili_2021_summer_evening_windy.webm',
  '/videos/banner/bili_2021_summer_night_clear.webm',
  '/videos/banner/bili_2021_summer_night_rainy.webm',
  '/videos/banner/bili_2021_summer_night_windy.webm',
];

// 用 useState 保证 SSR 与客户端随机索引一致，避免 hydration mismatch
const bannerIndex = useState('bannerIndex', () => Math.floor(Math.random() * bannerVideos.length));
const randomBanner = computed(() => bannerVideos[bannerIndex.value]);
</script>

<style scoped>
.bili-header__banner {
  position: relative;
  width: 100%;
  height: clamp(
    155px,
    calc(155px + max(0px, 100vw - 1640px) * 112 / 920),
    267px
  );
  overflow: hidden;
  background-color: var(--graph_bg_regular);
}

.banner-img {
  display: none;
}

.animated-banner {
  position: absolute;
  inset: 0;
}

.banner-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.banner-inner {
  position: absolute;
  inset: 0;
  z-index: 2;
  pointer-events: none;
}

.banner-logo {
  position: absolute;
  left: max(var(--layout-padding), calc((100% - 1980px) / 2));
  bottom: 36px;
  pointer-events: auto;
}

.banner-logo-img {
  height: 78px;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.3));
}

.taper-line {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 0;
  width: 100%;
  height: 100px;
  background: linear-gradient(rgba(0, 0, 0, 0.4), transparent);
  pointer-events: none;
}
</style>
