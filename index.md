---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: "🚀 Fast Pic Design"
  text: "快速构建图形编辑器"
  tagline: 一款基于Fabric + Vue3的开源Web图片编辑器
  actions:
    - theme: brand
      text: Get Started
      link: /guide/index
    - theme: alt
      text: View on GitHub
      link: https://github.com/nihaojob/vue-fabric-editor
  image:
    src: /public/main.png
    alt: VitePress

features:
  - icon: ⚙️
    title: 插件化架构
    details: 可自定义素材、右键菜单、快捷键等功能，易扩展。
  - icon: 🌂
    title: 简洁易用
    details: 以轻量、简洁为主的图形编辑器，而非大而全的在线PS类的重行设计工具。
  - icon: 🛍️
    title: 功能齐全
    details: 自定义模板、渐变、自定义字体等功能，满足轻量图片编辑场景。
  # - icon: 🚀
  #   title: Ship Fast Sites
  #   details: Fast initial load with static HTML, fast post-load navigation with client-side routing.
---


<style>
:root {
  --vp-home-hero-name-color: transparent;
  --vp-home-hero-name-background: -webkit-linear-gradient(120deg, #bd34fe 30%, #41d1ff);

  --vp-home-hero-image-background-image: linear-gradient(-45deg, #bd34fe 50%, #47caff 50%);
  --vp-home-hero-image-filter: blur(44px);
}

.icon{
  font-size: 30px;
}

@media (min-width: 640px) {
  :root {
    --vp-home-hero-image-filter: blur(56px);
  }
}

@media (min-width: 960px) {
  :root {
    --vp-home-hero-image-filter: blur(68px);
  }
}
</style>