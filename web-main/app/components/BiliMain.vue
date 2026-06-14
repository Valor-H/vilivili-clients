<template>
  <main class="bili-main">
    <section class="recommended-container">
      <div class="feed-header">
        <h2 class="feed-title">推荐视频</h2>
      </div>
      <div class="feed-grid">
        <article v-for="i in 12" :key="i" class="feed-card">
          <div class="card-image skeleton">
            <span class="placeholder-text">封面 {{ i }}</span>
          </div>
          <div class="card-info">
            <h3 class="card-title">视频标题示例 {{ i }}</h3>
            <div class="card-meta">
              <span class="up-name">UP主 {{ i }}</span>
              <span class="view-count">{{ i * 1.2 }}万观看</span>
            </div>
          </div>
        </article>
      </div>
    </section>
  </main>
</template>

<style scoped>
.recommended-container {
  width: 100%;
}

.feed-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.feed-title {
  font-size: 24px;
  font-weight: 700;
  color: var(--text1);
}

.feed-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 20px;
}

.feed-card {
  cursor: pointer;
  transition: transform 0.2s;
}

.feed-card:hover {
  transform: translateY(-4px);
}

.card-image {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 10;
  background-color: var(--graph_bg_regular);
  border-radius: 8px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 10px;
}

.placeholder-text {
  color: var(--text3);
  font-size: 14px;
}

.card-title {
  font-size: 15px;
  font-weight: 500;
  color: var(--text1);
  line-height: 1.5;
  margin-bottom: 6px;
  display: -webkit-box;
  line-clamp: 2;
  align-items: center;
  gap: 12px;
  font-size: 13px;
  color: var(--text3);
}
s
.up-name:hover {
  color: var(--brand_blue);
}
</style>
