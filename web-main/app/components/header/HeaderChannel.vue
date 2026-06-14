<template>
  <div class="bili-header__channel">
    <div class="channel-icons">
      <a
        v-for="item in channelIcons"
        :key="item.label"
        :href="item.href"
        target="_blank"
        class="channel-icons__item"
      >
        <div class="icon-bg" :style="{ background: item.gradient }">
          <img :src="item.icon" :alt="item.label" class="icon-img" />
        </div>
        <span class="icon-title">{{ item.label }}</span>
      </a>
    </div>

    <div class="right-channel-container">
      <div class="channel-items__left">
        <a
          v-for="cat in channelCategories"
          :key="cat"
          href="/category"
          class="channel-item"
        >
          {{ cat }}
        </a>
        <a href="/more" class="channel-item more">
          更多
          <img :src="moreIcon" alt="more" class="more-icon" />
        </a>
      </div>
      <div class="channel-items__right">
        <a
          v-for="item in channelExtra"
          :key="item.label"
          :href="item.href"
          class="extra-item"
        >
          <img v-if="item.icon" :src="item.icon" :alt="item.label" class="extra-icon" />
          {{ item.label }}
        </a>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import feedLightIcon from '~/assets/images/header/bili_feed_light.svg';
import favorateLightIcon from '~/assets/images/header/bili_favorate_light.svg';
import columnDarkIcon from '~/assets/images/header/bili_column_dark.svg';
import eventDarkIcon from '~/assets/images/header/bili_event_dark.svg';
import communityDarkIcon from '~/assets/images/header/bili_community_dark.svg';
import liveDarkIcon from '~/assets/images/header/bili_live_dark.svg';
import courseDarkIcon from '~/assets/images/header/bili_course_dark.svg';
import newSongsDarkIcon from '~/assets/images/header/bili_new_songs_dark.svg';
import moreIcon from '~/assets/images/header/bili_more_dark.svg';

const channelIcons = [
  {
    label: '动态',
    href: 'https://t.bilibili.com',
    icon: feedLightIcon,
    gradient: 'linear-gradient(135deg, #ff8c00, #ffaa00)',
  },
  {
    label: '热门',
    href: '/trending',
    icon: favorateLightIcon,
    gradient: 'linear-gradient(135deg, #fb7299, #ff85a7)',
  },
];

const channelCategories = [
  '番剧', '国创', '综艺', '动画', '鬼畜', '舞蹈',
  '娱乐', '科技数码', '美食', '汽车', '体育运动', 'vlog',
  '电影', '电视剧', '纪录片', '游戏', '音乐', '影视',
  '知识', '资讯', '小剧场', '时尚美妆', '动物',
];

const channelExtra = [
  { label: '专栏', href: '/column', icon: columnDarkIcon },
  { label: '活动', href: '/activity', icon: eventDarkIcon },
  { label: '社区中心', href: '/community', icon: communityDarkIcon },
  { label: '直播', href: '/live', icon: liveDarkIcon },
  { label: '课堂', href: '/class', icon: courseDarkIcon },
  { label: '新歌热榜', href: '/music', icon: newSongsDarkIcon },
];
</script>

<style scoped>
.bili-header__channel {
  display: flex;
  align-items: center;
  height: 120px;
  gap: 24px;
}

.channel-icons {
  display: flex;
  align-items: center;
  gap: 20px;
  flex-shrink: 0;
}

.channel-icons__item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--text1);
}

.icon-bg {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.2s;
}

.channel-icons__item:hover .icon-bg {
  transform: scale(1.08);
}

.icon-img {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.icon-title {
  font-size: 13px;
  color: var(--text2);
}

.right-channel-container {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 32px;
  min-width: 0;
}

.channel-items__left {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: repeat(2, 30px);
  grid-gap: 10px;
  flex: 1;
  min-width: 0;
}

.channel-item {
  box-sizing: border-box;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  padding: 0 4px;
  border: 1px solid var(--line_light);
  border-radius: 6px;
  background-color: var(--graph_bg_thin);
  color: var(--text2);
  font-size: 13px;
  line-height: 30px;
  white-space: nowrap;
  text-align: center;
  transition: background-color 0.3s, color 0.3s;
}

.channel-item:hover {
  color: var(--text1);
  background-color: var(--graph_bg_regular);
}

.channel-item.more {
  gap: 8px;
}

.more-icon {
  width: 10px;
  height: 10px;
  object-fit: contain;
}

@media (min-width: 1367px) {
  .channel-item,
  .extra-item {
    font-size: 14px;
  }
}

.channel-items__right {
  display: grid;
  grid-template-columns: repeat(3, auto);
  grid-template-rows: repeat(2, 30px);
  gap: 10px 6px;
  padding-left: 20px;
  border-left: 1px solid var(--line_regular);
  flex-shrink: 0;
}

.extra-item {
  box-sizing: border-box;
  display: inline-flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  height: 100%;
  gap: 6px;
  padding: 0 8px;
  border-radius: 6px;
  color: var(--text2);
  font-size: 13px;
  line-height: 30px;
  white-space: nowrap;
  transition: background-color 0.3s, color 0.3s;
}

.extra-item:hover {
  color: var(--text1);
  background-color: var(--graph_bg_thick);
}

.extra-icon {
  width: 20px;
  height: 20px;
  object-fit: contain;
}
</style>
