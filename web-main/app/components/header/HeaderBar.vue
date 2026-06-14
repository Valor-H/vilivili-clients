<template>
  <div class="bili-header__bar">
    <ul class="left-entry">
      <li class="entry-logo">
        <a href="/" class="logo-link">
          <img
            :src="logoImg"
            alt="bilibili"
            class="logo-img"
          />
        </a>
      </li>
      <li v-for="item in leftNavItems" :key="item.label">
        <a class="entry-title" :href="item.href">{{ item.label }}</a>
      </li>
      <li>
        <a class="entry-title download" href="/download">
          <svg class="download-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
            <polyline points="7 10 12 15 17 10" />
            <line x1="12" y1="15" x2="12" y2="3" />
          </svg>
          下载客户端
        </a>
      </li>
    </ul>

    <div class="center-search">
      <div class="nav-search-content">
        <input
          class="nav-search-input"
          type="text"
          placeholder="艾尔登法环菈妮支线"
        />
        <button class="nav-search-btn">
          <svg
            class="search-icon"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
          >
            <circle cx="11" cy="11" r="8" />
            <path d="m21 21-4.35-4.35" />
          </svg>
        </button>
      </div>
    </div>

    <ul class="right-entry">
      <li class="entry-user">
        <a href="/space" class="avatar-link">
          <div class="avatar">
            <img
              :src="avatarImg"
              alt="avatar"
              class="avatar-img"
            />
          </div>
        </a>
      </li>
      <li v-for="item in rightIconItems" :key="item.label">
        <a class="icon-link" :href="item.href">
          <img :src="item.icon" :alt="item.label" class="icon-img" />
          <span class="icon-text">{{ item.label }}</span>
        </a>
      </li>
      <li>
        <button class="header-upload-btn">
          <img
            :src="uploadImg"
            alt="upload"
            class="upload-icon"
          />
          投稿
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import logoImg from '~/assets/images/header/bili_icon_logo_light.svg';
import avatarImg from '~/assets/images/header/web-avatar-nav.avif';
import uploadImg from '~/assets/images/header/bili_upload_light.svg';
import vipImg from '~/assets/images/header/bili_vip_light.svg';
import msgImg from '~/assets/images/header/bili_msg_light.svg';
import feedImg from '~/assets/images/header/bili_feed_light.svg';
import favorateImg from '~/assets/images/header/bili_favorate_light.svg';
import historyImg from '~/assets/images/header/bili_history_light.svg';
import creatorImg from '~/assets/images/header/bili_creator_center_light.svg';

const leftNavItems = [
  { label: '首页', href: '/' },
  { label: '番剧', href: '/anime' },
  { label: '直播', href: '/live' },
  { label: '游戏中心', href: '/game' },
  { label: '会员购', href: '/mall' },
  { label: '漫画', href: '/manga' },
  { label: '赛事', href: '/match' },
  { label: '凡人', href: '/fanren' },
];

const rightIconItems = [
  { label: '大会员', href: '/vip', icon: vipImg },
  { label: '消息', href: '/message', icon: msgImg },
  { label: '动态', href: '/dynamic', icon: feedImg },
  { label: '收藏', href: '/favorite', icon: favorateImg },
  { label: '历史', href: '/history', icon: historyImg },
  { label: '创作中心', href: '/creator', icon: creatorImg },
];
</script>

<style scoped>
.bili-header__bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
  padding: 0 24px;
}

.left-entry,
.right-entry {
  display: flex;
  align-items: center;
  list-style: none;
  gap: 16px;
}

.left-entry {
  flex-shrink: 0;
  gap: 14px;
}

.entry-logo {
  margin-right: 4px;
}

.logo-link {
  display: block;
  width: 18px;
  height: 18px;
}

.logo-img {
  width: 18px;
  height: 18px;
  object-fit: contain;
}

.entry-title {
  color: var(--text1);
  font-size: 14px;
  font-weight: 500;
  transition: color 0.2s;
  white-space: nowrap;
}

.entry-title:hover {
  color: var(--brand_blue);
}

.download {
  display: inline-flex;
  align-items: center;
  gap: 4px;
}

.download-icon {
  width: 14px;
  height: 14px;
}

.center-search {
  flex: 1;
  max-width: 520px;
  margin: 0 24px;
}

.nav-search-content {
  display: flex;
  align-items: center;
  position: relative;
  z-index: 1;
  height: 40px;
  padding: 0 48px 0 4px;
  background-color: color-mix(in srgb, var(--graph_bg_regular) 90%, transparent);
  border: 1px solid var(--line_regular);
  border-radius: 8px;
  overflow: hidden;
  line-height: 38px;
  transition: background-color 0.3s, border-color 0.2s;
}

.nav-search-content:focus-within {
  background-color: var(--graph_bg_regular);
  border-color: var(--Ga4, #5e6267);
}

.nav-search-input {
  flex: 1;
  height: 100%;
  padding: 0 12px;
  background: transparent;
  border: none;
  outline: none;
  color: var(--text1);
  font-size: 14px;
}

.nav-search-input::placeholder {
  color: var(--text3);
}

.nav-search-btn {
  position: absolute;
  right: 0;
  top: 0;
  width: 48px;
  height: 100%;
  background: transparent;
  border: none;
  color: var(--text2);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color 0.2s;
}

.nav-search-btn:hover {
  color: var(--text1);
}

.search-icon {
  width: 18px;
  height: 18px;
}

.right-entry {
  flex-shrink: 0;
  gap: 18px;
}

.avatar-link {
  display: block;
}

.avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  overflow: hidden;
  background-color: var(--graph_bg_thick);
}

.avatar-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.icon-link {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  color: var(--text1);
  transition: color 0.2s;
}

.icon-link:hover {
  color: var(--brand_blue);
}

.icon-img {
  width: 20px;
  height: 20px;
  object-fit: contain;
}

.icon-text {
  font-size: 12px;
}

.header-upload-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  width: 90px;
  height: 36px;
  background-color: var(--brand_pink);
  border: none;
  border-radius: 8px;
  color: #fff;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.2s;
}

.header-upload-btn:hover {
  background-color: var(--brand_pink_light);
}

.upload-icon {
  width: 18px;
  height: 18px;
}
</style>
