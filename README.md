<!--
  古风水墨 GitHub 个人主页 v2.0.0
  作者：cubeyu
  重构说明：
    旧版（v1.0.0）大量使用 style="..." / class="..." / <style> / <link>，
    但 GitHub HTML 过滤器会完全移除这些，导致主页在 GitHub 上塌成默认样式。
    v2.0.0 改为：
      1. 完全不使用 style / class / <style> / <link>（GitHub 会过滤）
      2. 关键文字（标题 / 印章 / 章节名）用内联 <svg><text font-family="..."> 嵌入
         font-family 走"系统古风字体兜底链"，Windows/macOS 用户可看到楷体/仿宋
      3. 卡片布局用 <table> 的 bgcolor / cellpadding / cellspacing / align 等允许属性
      4. 水墨元素（远山 / 墨竹 / 印章 / 分割线）全部内联 SVG，GitHub 完整渲染
      5. 正文字体交给 GitHub 默认，用 emoji / Unicode 符号营造古风意境
    字体兜底链：STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, STSong, SimSun, 宋体, serif
-->

<!-- ============ 顶部 Banner：水墨山水卷轴 ============ -->
<div align="center">
  <img src="https://trae-api-cn.mchost.guru/api/ide/v1/text_to_image?prompt=Chinese%20traditional%20ink%20wash%20painting%2C%20misty%20mountains%20and%20rivers%2C%20distant%20peaks%20in%20fog%2C%20a%20small%20boat%20on%20calm%20water%2C%20minimalist%20sumi-e%20style%2C%20monochrome%20black%20ink%20on%20rice%20paper%2C%20elegant%20and%20serene&image_size=landscape_16_9" width="100%" alt="水墨山水卷轴" />
</div>

<!-- ============ 主标题区（SVG 嵌入楷体，GitHub 完整渲染） ============ -->
<div align="center">
  <svg width="560" height="130" viewBox="0 0 560 130" xmlns="http://www.w3.org/2000/svg">
    <!-- 主标题：墨客 · cubeyu -->
    <text x="280" y="62" text-anchor="middle" fill="#1a1a1a" font-size="56" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, STSong, SimSun, 宋体, serif" font-weight="bold" letter-spacing="8">墨客 · cubeyu</text>
    <!-- 副标题 -->
    <text x="280" y="98" text-anchor="middle" fill="#5a4632" font-size="20" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" letter-spacing="6">一蓑烟雨任平生 · 亦 coding 亦逍遥</text>
    <!-- 引言 -->
    <text x="280" y="122" text-anchor="middle" fill="#8b6f48" font-size="14" font-family="STFangsong, FangSong, 仿宋, STKaiti, KaiTi, 楷体, serif" font-style="italic" letter-spacing="3">纸上得来终觉浅，绝知此事要躬行</text>
  </svg>
</div>

<!-- ============ 朱砂分割线 + 印章（SVG 内嵌） ============ -->
<div align="center">
  <svg width="340" height="48" viewBox="0 0 340 48" xmlns="http://www.w3.org/2000/svg">
    <!-- 双曲线水墨横线 -->
    <path d="M10 24 Q 85 18 170 24 T 330 24" stroke="#2c2c2c" stroke-width="1.5" fill="none" opacity="0.7"/>
    <path d="M10 24 Q 85 30 170 24 T 330 24" stroke="#1a1a1a" stroke-width="0.8" fill="none" opacity="0.5"/>
    <!-- 朱砂方印 -->
    <rect x="152" y="9" width="30" height="30" fill="#a83232" rx="2"/>
    <text x="167" y="30" text-anchor="middle" fill="#f5f0e6" font-size="14" font-family="STFangsong, FangSong, 仿宋, serif" font-weight="bold">墨</text>
  </svg>
</div>

<!-- ============ 卡片 1：吾之简介 ============ -->
<!-- 外层 table 做边框色，内层 table 做卡片背景色（GitHub 允许 bgcolor/cellpadding） -->
<table align="center" bgcolor="#c9b88a" cellpadding="0" cellspacing="0" width="92%">
<tr><td>
<table bgcolor="#f7f1e3" cellpadding="24" cellspacing="0" width="100%">
<tr><td>

<!-- 章节标题（SVG 嵌入楷体） -->
<div align="center">
  <svg width="220" height="44" viewBox="0 0 220 44" xmlns="http://www.w3.org/2000/svg">
    <text x="110" y="30" text-anchor="middle" fill="#3a2a1a" font-size="28" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" font-weight="bold" letter-spacing="6">◈ 吾之简介</text>
    <line x1="20" y1="38" x2="200" y2="38" stroke="#8b1a1a" stroke-width="1.5"/>
  </svg>
</div>

余乃 **cubeyu**，居于代码之境，游走于字节之间。

喜古风之雅致，爱水墨之意韵；亦恋 `code` 之精巧，乐 `开源` 之共济。

愿以键盘为笔，以屏幕为纸，书一行行山水，绘一帧帧春秋。

<div align="center">
  <img src="https://img.shields.io/badge/岁月-数字游民-a83232?style=flat-square&labelColor=ede0c6" alt="岁月" />
  <img src="https://img.shields.io/badge/志向-技术布道者-2c2c2c?style=flat-square&labelColor=ede0c6" alt="志向" />
  <img src="https://img.shields.io/badge/心境-闲云野鹤-5a4632?style=flat-square&labelColor=ede0c6" alt="心境" />
</div>

</td></tr>
</table>
</td></tr>
</table>

<!-- 卡片间距 -->
<div align="center">&nbsp;</div>

<!-- ============ 卡片 2：所学技艺 ============ -->
<table align="center" bgcolor="#c9b88a" cellpadding="0" cellspacing="0" width="92%">
<tr><td>
<table bgcolor="#f7f1e3" cellpadding="24" cellspacing="0" width="100%">
<tr><td>

<div align="center">
  <svg width="220" height="44" viewBox="0 0 220 44" xmlns="http://www.w3.org/2000/svg">
    <text x="110" y="30" text-anchor="middle" fill="#3a2a1a" font-size="28" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" font-weight="bold" letter-spacing="6">◈ 所学技艺</text>
    <line x1="20" y1="38" x2="200" y2="38" stroke="#8b1a1a" stroke-width="1.5"/>
  </svg>
</div>

**🗡 剑修（语言）：**

<p align="center">
  <img src="https://img.shields.io/badge/JavaScript-墨色-1a1a1a?style=flat-square&logo=javascript&logoColor=f7df1e" alt="JS" />
  <img src="https://img.shields.io/badge/TypeScript-墨色-1a1a1a?style=flat-square&logo=typescript&logoColor=3178c6" alt="TS" />
  <img src="https://img.shields.io/badge/Python-墨色-1a1a1a?style=flat-square&logo=python&logoColor=3776ab" alt="Python" />
  <img src="https://img.shields.io/badge/Go-墨色-1a1a1a?style=flat-square&logo=go&logoColor=00add8" alt="Go" />
</p>

**🏛 阵法（框架）：**

<p align="center">
  <img src="https://img.shields.io/badge/React-朱砂-a83232?style=flat-square&logo=react&logoColor=61dafb" alt="React" />
  <img src="https://img.shields.io/badge/Vue-朱砂-a83232?style=flat-square&logo=vue.js&logoColor=42b883" alt="Vue" />
  <img src="https://img.shields.io/badge/Node.js-朱砂-a83232?style=flat-square&logo=node.js&logoColor=339933" alt="Node" />
  <img src="https://img.shields.io/badge/Next.js-朱砂-a83232?style=flat-square&logo=next.js&logoColor=000000" alt="Next" />
</p>

**🏺 器物（工具）：**

<p align="center">
  <img src="https://img.shields.io/badge/Git-青墨-5a4632?style=flat-square&logo=git&logoColor=f05032" alt="Git" />
  <img src="https://img.shields.io/badge/Docker-青墨-5a4632?style=flat-square&logo=docker&logoColor=2496ed" alt="Docker" />
  <img src="https://img.shields.io/badge/Linux-青墨-5a4632?style=flat-square&logo=linux&logoColor=fcc624" alt="Linux" />
  <img src="https://img.shields.io/badge/VSCode-青墨-5a4632?style=flat-square&logo=visual-studio-code&logoColor=007acc" alt="VSCode" />
</p>

</td></tr>
</table>
</td></tr>
</table>

<div align="center">&nbsp;</div>

<!-- ============ 卡片 3：得意之作 ============ -->
<table align="center" bgcolor="#c9b88a" cellpadding="0" cellspacing="0" width="92%">
<tr><td>
<table bgcolor="#f7f1e3" cellpadding="24" cellspacing="0" width="100%">
<tr><td>

<div align="center">
  <svg width="220" height="44" viewBox="0 0 220 44" xmlns="http://www.w3.org/2000/svg">
    <text x="110" y="30" text-anchor="middle" fill="#3a2a1a" font-size="28" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" font-weight="bold" letter-spacing="6">◈ 得意之作</text>
    <line x1="20" y1="38" x2="200" y2="38" stroke="#8b1a1a" stroke-width="1.5"/>
  </svg>
</div>

📂 **[project-one](#)**  
　—— 一方天地，可窥星辰大海（此处替换为项目描述）

📂 **[project-two](#)**  
　—— 半卷诗书，藏尽人间烟火（此处替换为项目描述）

📂 **[project-three](#)**  
　—— 一壶清酒，醉看代码生花（此处替换为项目描述）

<div align="center">
  <img src="https://img.shields.io/badge/更多作品-敬请移步仓库-a83232?style=flat-square&labelColor=ede0c6" alt="更多作品" />
</div>

</td></tr>
</table>
</td></tr>
</table>

<div align="center">&nbsp;</div>

<!-- ============ 卡片 4：笔耕不辍（GitHub 统计） ============ -->
<table align="center" bgcolor="#c9b88a" cellpadding="0" cellspacing="0" width="92%">
<tr><td>
<table bgcolor="#f7f1e3" cellpadding="24" cellspacing="0" width="100%">
<tr><td>

<div align="center">
  <svg width="220" height="44" viewBox="0 0 220 44" xmlns="http://www.w3.org/2000/svg">
    <text x="110" y="30" text-anchor="middle" fill="#3a2a1a" font-size="28" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" font-weight="bold" letter-spacing="6">◈ 笔耕不辍</text>
    <line x1="20" y1="38" x2="200" y2="38" stroke="#8b1a1a" stroke-width="1.5"/>
  </svg>
</div>

<div align="center">
  <img height="160" src="https://github-readme-stats.vercel.app/api?username=cubeyu&show_icons=true&theme=graywhite&bg_color=f7f1e3,ede0c6&title_color=3a2a1a&text_color=2c2c2c&icon_color=a83232&border_color=c9b88a&hide_border=false&count_private=true" alt="GitHub Stats" />
  <br />
  <img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=cubeyu&layout=compact&theme=graywhite&bg_color=f7f1e3,ede0c0&title_color=3a2a1a&text_color=2c2c2c&border_color=c9b88a" alt="Top Languages" />
  <br />
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=cubeyu&theme=graywhite&background=f7f1e3&stroke=c9b88a&ring=8b1a1a&fire=a83232&currStreakLabel=3a2a1a&sideNums=2c2c2c&currStreakNum=a83232&dates=5a4632" alt="Streak Stats" />
</div>

</td></tr>
</table>
</td></tr>
</table>

<div align="center">&nbsp;</div>

<!-- ============ 卡片 5：鸿雁传书 ============ -->
<table align="center" bgcolor="#c9b88a" cellpadding="0" cellspacing="0" width="92%">
<tr><td>
<table bgcolor="#f7f1e3" cellpadding="24" cellspacing="0" width="100%">
<tr><td>

<div align="center">
  <svg width="220" height="44" viewBox="0 0 220 44" xmlns="http://www.w3.org/2000/svg">
    <text x="110" y="30" text-anchor="middle" fill="#3a2a1a" font-size="28" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" font-weight="bold" letter-spacing="6">◈ 鸿雁传书</text>
    <line x1="20" y1="38" x2="200" y2="38" stroke="#8b1a1a" stroke-width="1.5"/>
  </svg>
</div>

<div align="center">
  <a href="https://github.com/cubeyu">
    <img src="https://img.shields.io/badge/GitHub-墨客居所-1a1a1a?style=for-the-badge&logo=github&logoColor=f5f0e6&labelColor=a83232" alt="GitHub" />
  </a>
  <br />
  <br />
  <a href="mailto:your-email@example.com">
    <img src="https://img.shields.io/badge/Email-飞鸽传书-a83232?style=for-the-badge&logo=gmail&logoColor=f5f0e6&labelColor=1a1a1a" alt="Email" />
  </a>
</div>

<div align="center">
  <svg width="420" height="34" viewBox="0 0 420 34" xmlns="http://www.w3.org/2000/svg">
    <text x="210" y="24" text-anchor="middle" fill="#5a4632" font-size="16" font-family="STFangsong, FangSong, 仿宋, STKaiti, KaiTi, 楷体, serif" font-style="italic" letter-spacing="4">山高水长，江湖再见 · 期待与你共话技术春秋</text>
  </svg>
</div>

</td></tr>
</table>
</td></tr>
</table>

<!-- ============ 底部：墨竹 + 朱砂落款印章（全 SVG） ============ -->
<div align="center">
  <svg width="420" height="110" viewBox="0 0 420 110" xmlns="http://www.w3.org/2000/svg">
    <!-- 墨竹竿 -->
    <path d="M50 105 Q 52 60 55 18" stroke="#1a1a1a" stroke-width="3.5" fill="none" opacity="0.85"/>
    <!-- 竹节 -->
    <circle cx="52" cy="85" r="3" fill="#1a1a1a" opacity="0.85"/>
    <circle cx="53" cy="60" r="3" fill="#1a1a1a" opacity="0.85"/>
    <circle cx="54" cy="35" r="3" fill="#1a1a1a" opacity="0.85"/>
    <!-- 竹叶 -->
    <path d="M55 30 Q 75 22 95 27 Q 78 34 55 30 Z" fill="#2c2c2c" opacity="0.8"/>
    <path d="M54 48 Q 32 36 12 42 Q 28 50 54 48 Z" fill="#1a1a1a" opacity="0.85"/>
    <path d="M53 65 Q 72 56 95 62 Q 76 70 53 65 Z" fill="#2c2c2c" opacity="0.75"/>
    <path d="M55 22 Q 72 10 92 13 Q 74 22 55 22 Z" fill="#1a1a1a" opacity="0.9"/>
    <path d="M54 78 Q 30 70 12 75 Q 28 82 54 78 Z" fill="#2c2c2c" opacity="0.7"/>

    <!-- 中间题字 -->
    <text x="210" y="60" text-anchor="middle" fill="#5a4632" font-size="20" font-family="STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, serif" letter-spacing="6">纸短情长 · 码海无垠</text>

    <!-- 朱砂落款印章 -->
    <rect x="340" y="50" width="50" height="50" fill="#a83232" rx="3" opacity="0.92"/>
    <text x="365" y="72" text-anchor="middle" fill="#f5f0e6" font-size="14" font-family="STFangsong, FangSong, 仿宋, serif" font-weight="bold">cubeyu</text>
    <text x="365" y="90" text-anchor="middle" fill="#f5f0e6" font-size="11" font-family="STFangsong, FangSong, 仿宋, serif">墨印</text>
  </svg>
</div>

<!-- ============ 文末签名 ============ -->
<div align="center">
  <svg width="320" height="28" viewBox="0 0 320 28" xmlns="http://www.w3.org/2000/svg">
    <text x="160" y="20" text-anchor="middle" fill="#8b6f48" font-size="13" font-family="STFangsong, FangSong, 仿宋, STKaiti, KaiTi, 楷体, serif" font-style="italic" letter-spacing="6">— cubeyu 制 · 岁次丙午 —</text>
  </svg>
</div>

<!-- ============ 折叠区：关于本次设计（details 在 GitHub 上原生支持） ============ -->
<details>
<summary>📜 关于本主页的设计说明（点击展开）</summary>

**字体策略**

GitHub README 的 HTML 过滤器会移除 `style` / `class` / `<style>` / `<link>` 等 CSS 渲染入口，因此**普通文字无法直接改成古风字体**。

本主页的关键文字（主标题、副标题、章节名、印章、引言、落款）均采用**内联 SVG `<text>` 元素**，通过 SVG 表现属性 `font-family` 指定系统古风字体兜底链：

```
STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, STSong, SimSun, 宋体, serif
```

- Windows 用户：可看到楷体（KaiTi）/ 仿宋（FangSong）
- macOS 用户：可看到华文楷体（STKaiti）/ 华文仿宋（STFangsong）
- Linux 用户：若未安装中文字体，会回退到默认 serif

**卡片实现**

卡片背景与边框通过嵌套 `<table>` 配合 `bgcolor` / `cellpadding` / `cellspacing` / `align` / `width` 等 HTML4 属性实现，这些属性在 GitHub 的 sanitizer 白名单内。

**水墨元素**

远山、墨竹、印章、分割线均为内联 SVG，无外部依赖，GitHub 完整渲染。

**完整古风字体效果**

如需欣赏完整的 Google Fonts 古风字体（如「志莽行」「马善政」「龙藏」），请查看 [preview.html](./preview.html)。

</details>
