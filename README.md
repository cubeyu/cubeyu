<!--
  古风水墨 GitHub 个人主页 v3.0.0
  作者：cubeyu
  
  关键发现（v2.0.0 失败原因）：
    GitHub 的 sanitization_filter.rb 白名单：
    - 允许的元素：h1-h8, br, b, i, strong, em, a, pre, code, img, tt, div, ins, del, sup, sub,
      p, ol, ul, table, thead, tbody, tfoot, blockquote, dl, dt, dd, kbd, q, samp, var, hr,
      ruby, rt, rp, li, tr, td, th, s, strike, summary, details, caption, figure, figcaption,
      abbr, bdo, cite, dfn, mark, small, span, time, wbr
    - 注意：没有 <svg>！没有 <path>！没有 <text>！内联 SVG 会被完全移除！
    - 属性白名单（all）：abbr, accept, accept-charset, accesskey, action, align, alt,
      aria-describedby, aria-hidden, aria-label, aria-labelledby, axis, border, cellpadding,
      cellspacing, char, charoff, charset, checked, clear, cols, colspan, color, compact,
      coords, datetime, dir, disabled, enctype, for, frame, headers, height, hreflang,
      hspace, ismap, label, lang, maxlength, media, method, multiple, name, nohref, noshade,
      nowrap, open, prompt, readonly, rel, rev, rows, rowspan, rules, scope, selected, shape,
      size, span, start, summary, tabindex, target, title, type, usemap, valign, value,
      vspace, width, itemprop
    - 注意：没有 'bgcolor'！没有 'style'！没有 'class'！
    - 但 <img src="..."> 完全允许，包括 data: URI 协议！
  
  v3.0.0 策略（实测可用）：
    1. 所有水墨装饰（标题/分割线/墨竹/印章/章节标题）转成 Base64 SVG 图片
       用 <img src="data:image/svg+xml;base64,..."> 引用，GitHub 完整渲染
    2. 卡片用 Markdown 表格结构 + 章节标题图片营造古风分区感
    3. 徽章用 Shields.io 动态生成
    4. SVG 内 font-family 走系统古风字体兜底链
       (STKaiti/KaiTi/楷体/STFangsong/FangSong/仿宋/STSong/SimSun/宋体/serif)
    5. 顶部水墨山水横幅用 base64 内嵌，不依赖外部图片服务
-->

<!-- ============ 顶部 Banner：水墨山水卷轴（Base64 SVG） ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI4ODAiIGhlaWdodD0iMjQwIiB2aWV3Qm94PSIwIDAgODgwIDI0MCI+CiAgPCEtLSDlrqPnurjlupXoibIgLS0+CiAgPHJlY3Qgd2lkdGg9Ijg4MCIgaGVpZ2h0PSIyNDAiIGZpbGw9IiNmN2YxZTMiLz4KICAKICA8IS0tIOi/nOWxse+8iOa1k+WiqO+8iSAtLT4KICA8cGF0aCBkPSJNMCAxODAgUSAxMDAgMTIwIDIwMCAxNTAgVCA0MDAgMTMwIFQgNjAwIDE1NSBUIDg4MCAxNDAgTCA4ODAgMjQwIEwgMCAyNDAgWiIgZmlsbD0iIzFhMWExYSIgb3BhY2l0eT0iMC4xOCIvPgogIAogIDwhLS0g5Lit6L+c5bGxIC0tPgogIDxwYXRoIGQ9Ik0wIDIwMCBRIDEyMCAxNjAgMjQwIDE4MCBUIDQ4MCAxNjUgVCA3MjAgMTg1IFQgODgwIDE3NSBMIDg4MCAyNDAgTCAwIDI0MCBaIiBmaWxsPSIjMWExYTFhIiBvcGFjaXR5PSIwLjI4Ii8+CiAgCiAgPCEtLSDov5HlsbEgLS0+CiAgPHBhdGggZD0iTTAgMjIwIFEgODAgMTgwIDE4MCAyMDAgVCAzODAgMTkwIFQgNTgwIDIwNSBUIDg4MCAxOTUgTCA4ODAgMjQwIEwgMCAyNDAgWiIgZmlsbD0iIzFhMWExYSIgb3BhY2l0eT0iMC40NSIvPgogIAogIDwhLS0g6Zu+5rCUIC0tPgogIDxlbGxpcHNlIGN4PSIzMDAiIGN5PSIxNjAiIHJ4PSIxODAiIHJ5PSIxNCIgZmlsbD0iI2Y1ZjBlNiIgb3BhY2l0eT0iMC42Ii8+CiAgPGVsbGlwc2UgY3g9IjY1MCIgY3k9IjE3MCIgcng9IjE2MCIgcnk9IjEyIiBmaWxsPSIjZjVmMGU2IiBvcGFjaXR5PSIwLjU1Ii8+CiAgCiAgPCEtLSDmsLTpnaIgLS0+CiAgPHBhdGggZD0iTTAgMjI1IEwgODgwIDIyNSBMIDg4MCAyNDAgTCAwIDI0MCBaIiBmaWxsPSIjMWExYTFhIiBvcGFjaXR5PSIwLjAzIi8+CiAgCiAgPCEtLSDmsLTms6IgLS0+CiAgPHBhdGggZD0iTTM4MCAyMjUgUSAzOTUgMjIyIDQxMCAyMjUgVCA0NDAgMjI1IFQgNDcwIDIyNSIgc3Ryb2tlPSIjMWExYTFhIiBzdHJva2Utd2lkdGg9IjAuNiIgZmlsbD0ibm9uZSIgb3BhY2l0eT0iMC40Ii8+CiAgPHBhdGggZD0iTTQ2MCAyMzAgUSA0NzUgMjI3IDQ5MCAyMzAgVCA1MjAgMjMwIiBzdHJva2U9IiMxYTFhMWEiIHN0cm9rZS13aWR0aD0iMC42IiBmaWxsPSJub25lIiBvcGFjaXR5PSIwLjM1Ii8+CiAgPHBhdGggZD0iTTUyMCAyMzMgUSA1MzUgMjMwIDU1MCAyMzMgVCA1ODAgMjMzIiBzdHJva2U9IiMxYTFhMWEiIHN0cm9rZS13aWR0aD0iMC42IiBmaWxsPSJub25lIiBvcGFjaXR5PSIwLjMiLz4KICAKICA8IS0tIOWtpOiInyAtLT4KICA8cGF0aCBkPSJNNDEwIDIxOCBRIDQyNSAyMTQgNDQwIDIxOCBMIDQzOCAyMjIgUSA0MjUgMjIwIDQxMiAyMjIgWiIgZmlsbD0iIzFhMWExYSIgb3BhY2l0eT0iMC43Ii8+CiAgPGxpbmUgeDE9IjQyNSIgeTE9IjIxOCIgeDI9IjQyNSIgeTI9IjIwMCIgc3Ryb2tlPSIjMWExYTFhIiBzdHJva2Utd2lkdGg9IjEiIG9wYWNpdHk9IjAuNyIvPgogIAogIDwhLS0g6aOe6bifIC0tPgogIDxwYXRoIGQ9Ik01NjAgODAgUSA1NjUgNzYgNTcwIDgwIFEgNTc1IDc2IDU4MCA4MCIgc3Ryb2tlPSIjMWExYTFhIiBzdHJva2Utd2lkdGg9IjEuMiIgZmlsbD0ibm9uZSIgb3BhY2l0eT0iMC42Ii8+CiAgPHBhdGggZD0iTTYyMCA2MCBRIDYyNSA1NiA2MzAgNjAgUSA2MzUgNTYgNjQwIDYwIiBzdHJva2U9IiMxYTFhMWEiIHN0cm9rZS13aWR0aD0iMS4yIiBmaWxsPSJub25lIiBvcGFjaXR5PSIwLjUiLz4KICAKICA8IS0tIOmimOWtl++8muWxseawtOacieebuOmAoiAtLT4KICA8dGV4dCB4PSI2MCIgeT0iNjAiIGZpbGw9IiMxYTFhMWEiIG9wYWNpdHk9IjAuNSIgZm9udC1zaXplPSIyMiIgZm9udC1mYW1pbHk9IlNUS2FpdGksIEthaVRpLCDmpbfkvZMsIHNlcmlmIj7lsbE8L3RleHQ+CiAgPHRleHQgeD0iNjAiIHk9Ijg4IiBmaWxsPSIjMWExYTFhIiBvcGFjaXR5PSIwLjUiIGZvbnQtc2l6ZT0iMjIiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBzZXJpZiI+5rC0PC90ZXh0PgogIDx0ZXh0IHg9IjYwIiB5PSIxMTYiIGZpbGw9IiMxYTFhMWEiIG9wYWNpdHk9IjAuNSIgZm9udC1zaXplPSIyMiIgZm9udC1mYW1pbHk9IlNUS2FpdGksIEthaVRpLCDmpbfkvZMsIHNlcmlmIj7mnIk8L3RleHQ+CiAgPHRleHQgeD0iNjAiIHk9IjE0NCIgZmlsbD0iIzFhMWExYSIgb3BhY2l0eT0iMC41IiBmb250LXNpemU9IjIyIiBmb250LWZhbWlseT0iU1RLYWl0aSwgS2FpVGksIOalt+S9kywgc2VyaWYiPuebuDwvdGV4dD4KICA8dGV4dCB4PSI2MCIgeT0iMTcyIiBmaWxsPSIjMWExYTFhIiBvcGFjaXR5PSIwLjUiIGZvbnQtc2l6ZT0iMjIiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBzZXJpZiI+6YCiPC90ZXh0PgogIAogIDwhLS0g5pyx56CC5Y2wIC0tPgogIDxyZWN0IHg9IjU2IiB5PSIxODYiIHdpZHRoPSIzMiIgaGVpZ2h0PSIzMiIgZmlsbD0iI2E4MzIzMiIgb3BhY2l0eT0iMC44NSIgcng9IjIiLz4KICA8dGV4dCB4PSI3MiIgeT0iMjA4IiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSIjZjVmMGU2IiBmb250LXNpemU9IjE0IiBmb250LWZhbWlseT0iU1RGYW5nc29uZywgRmFuZ1NvbmcsIOS7v+Wuiywgc2VyaWYiIGZvbnQtd2VpZ2h0PSJib2xkIj7loqg8L3RleHQ+CiAgCiAgPCEtLSDovrnmoYYgLS0+CiAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9Ijg3NiIgaGVpZ2h0PSIyMzYiIGZpbGw9Im5vbmUiIHN0cm9rZT0iI2M5Yjg4YSIgc3Ryb2tlLXdpZHRoPSIxIi8+Cjwvc3ZnPgo=" width="100%" alt="水墨山水卷轴" />
</div>

<br/>

<!-- ============ 主标题（Base64 SVG 图片） ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI2MDAiIGhlaWdodD0iMTQwIiB2aWV3Qm94PSIwIDAgNjAwIDE0MCI+CiAgPCEtLSDkuLvmoIfpopjvvJrloqjlrqIgwrcgY3ViZXl1IC0tPgogIDx0ZXh0IHg9IjMwMCIgeT0iNjUiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMxYTFhMWEiIGZvbnQtc2l6ZT0iNTYiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI4Ij7loqjlrqIgwrcgY3ViZXl1PC90ZXh0PgogIDwhLS0g5Ymv5qCH6aKYIC0tPgogIDx0ZXh0IHg9IjMwMCIgeT0iMTAyIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSIjNWE0NjMyIiBmb250LXNpemU9IjIwIiBmb250LWZhbWlseT0iU1RLYWl0aSwgS2FpVGksIOalt+S9kywgU1RGYW5nc29uZywgRmFuZ1NvbmcsIOS7v+Wuiywgc2VyaWYiIGxldHRlci1zcGFjaW5nPSI2Ij7kuIDok5Hng5/pm6jku7vlubPnlJ8gwrcg5LqmIGNvZGluZyDkuqbpgI3pgaU8L3RleHQ+CiAgPCEtLSDlvJXoqIAgLS0+CiAgPHRleHQgeD0iMzAwIiB5PSIxMjgiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiM4YjZmNDgiIGZvbnQtc2l6ZT0iMTQiIGZvbnQtZmFtaWx5PSJTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBzZXJpZiIgZm9udC1zdHlsZT0iaXRhbGljIiBsZXR0ZXItc3BhY2luZz0iMyI+57q45LiK5b6X5p2l57uI6KeJ5rWF77yM57ud55+l5q2k5LqL6KaB6Lqs6KGMPC90ZXh0Pgo8L3N2Zz4K" width="600" height="140" alt="墨客 · cubeyu" />
</div>

<br/>

<!-- ============ 朱砂分割线 + 印章（Base64 SVG） ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIzNjAiIGhlaWdodD0iNTAiIHZpZXdCb3g9IjAgMCAzNjAgNTAiPgogIDwhLS0g5Y+M5puy57q/5rC05aKo5qiq57q/IC0tPgogIDxwYXRoIGQ9Ik0xMCAyNSBRIDkwIDE4IDE4MCAyNSBUIDM1MCAyNSIgc3Ryb2tlPSIjMmMyYzJjIiBzdHJva2Utd2lkdGg9IjEuNSIgZmlsbD0ibm9uZSIgb3BhY2l0eT0iMC43Ii8+CiAgPHBhdGggZD0iTTEwIDI1IFEgOTAgMzIgMTgwIDI1IFQgMzUwIDI1IiBzdHJva2U9IiMxYTFhMWEiIHN0cm9rZS13aWR0aD0iMC44IiBmaWxsPSJub25lIiBvcGFjaXR5PSIwLjUiLz4KICA8IS0tIOacseegguaWueWNsCAtLT4KICA8cmVjdCB4PSIxNjAiIHk9IjEwIiB3aWR0aD0iMzIiIGhlaWdodD0iMzIiIGZpbGw9IiNhODMyMzIiIHJ4PSIyIi8+CiAgPHRleHQgeD0iMTc2IiB5PSIzMSIgdGV4dC1hbmNob3I9Im1pZGRsZSIgZmlsbD0iI2Y1ZjBlNiIgZm9udC1zaXplPSIxNSIgZm9udC1mYW1pbHk9IlNURmFuZ3NvbmcsIEZhbmdTb25nLCDku7/lrossIHNlcmlmIiBmb250LXdlaWdodD0iYm9sZCI+5aKoPC90ZXh0Pgo8L3N2Zz4K" width="360" height="50" alt="分割线" />
</div>

<br/>

<!-- ============ 吾之简介 ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNDAiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCAyNDAgNDgiPjx0ZXh0IHg9IjEyMCIgeT0iMzIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMzYTJhMWEiIGZvbnQtc2l6ZT0iMjgiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI2Ij7il4gg5ZC+5LmL566A5LuLPC90ZXh0PjxsaW5lIHgxPSIyMCIgeTE9IjQyIiB4Mj0iMjIwIiB5Mj0iNDIiIHN0cm9rZT0iIzhiMWExYSIgc3Ryb2tlLXdpZHRoPSIxLjUiLz48L3N2Zz4=" width="240" height="48" alt="◈ 吾之简介" />
</div>

余乃 **cubeyu**，居于代码之境，游走于字节之间。

喜古风之雅致，爱水墨之意韵；亦恋 `code` 之精巧，乐 `开源` 之共济。

愿以键盘为笔，以屏幕为纸，书一行行山水，绘一帧帧春秋。

<p align="center">
  <img src="https://img.shields.io/badge/岁月-数字游民-a83232?style=flat-square&labelColor=ede0c6" alt="岁月" />
  <img src="https://img.shields.io/badge/志向-技术布道者-2c2c2c?style=flat-square&labelColor=ede0c6" alt="志向" />
  <img src="https://img.shields.io/badge/心境-闲云野鹤-5a4632?style=flat-square&labelColor=ede0c6" alt="心境" />
</p>

<br/>

<!-- ============ 所学技艺 ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNDAiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCAyNDAgNDgiPjx0ZXh0IHg9IjEyMCIgeT0iMzIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMzYTJhMWEiIGZvbnQtc2l6ZT0iMjgiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI2Ij7il4gg5omA5a2m5oqA6Im6PC90ZXh0PjxsaW5lIHgxPSIyMCIgeTE9IjQyIiB4Mj0iMjIwIiB5Mj0iNDIiIHN0cm9rZT0iIzhiMWExYSIgc3Ryb2tlLXdpZHRoPSIxLjUiLz48L3N2Zz4=" width="240" height="48" alt="◈ 所学技艺" />
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

<br/>

<!-- ============ 得意之作 ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNDAiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCAyNDAgNDgiPjx0ZXh0IHg9IjEyMCIgeT0iMzIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMzYTJhMWEiIGZvbnQtc2l6ZT0iMjgiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI2Ij7il4gg5b6X5oSP5LmL5L2cPC90ZXh0PjxsaW5lIHgxPSIyMCIgeTE9IjQyIiB4Mj0iMjIwIiB5Mj0iNDIiIHN0cm9rZT0iIzhiMWExYSIgc3Ryb2tlLXdpZHRoPSIxLjUiLz48L3N2Zz4=" width="240" height="48" alt="◈ 得意之作" />
</div>

📂 **[project-one](https://github.com/cubeyu)** —— 一方天地，可窥星辰大海

📂 **[project-two](https://github.com/cubeyu)** —— 半卷诗书，藏尽人间烟火

📂 **[project-three](https://github.com/cubeyu)** —— 一壶清酒，醉看代码生花

<p align="center">
  <img src="https://img.shields.io/badge/更多作品-敬请移步仓库-a83232?style=flat-square&labelColor=ede0c6" alt="更多作品" />
</p>

<br/>

<!-- ============ 笔耕不辍 ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNDAiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCAyNDAgNDgiPjx0ZXh0IHg9IjEyMCIgeT0iMzIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMzYTJhMWEiIGZvbnQtc2l6ZT0iMjgiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI2Ij7il4gg56yU6ICV5LiN6L6NPC90ZXh0PjxsaW5lIHgxPSIyMCIgeTE9IjQyIiB4Mj0iMjIwIiB5Mj0iNDIiIHN0cm9rZT0iIzhiMWExYSIgc3Ryb2tlLXdpZHRoPSIxLjUiLz48L3N2Zz4=" width="240" height="48" alt="◈ 笔耕不辍" />
</div>

<p align="center">
  <img height="160" src="https://github-readme-stats.vercel.app/api?username=cubeyu&show_icons=true&theme=graywhite&bg_color=f7f1e3,ede0c6&title_color=3a2a1a&text_color=2c2c2c&icon_color=a83232&border_color=c9b88a&hide_border=false&count_private=true" alt="GitHub Stats" />
</p>

<p align="center">
  <img height="160" src="https://github-readme-stats.vercel.app/api/top-langs/?username=cubeyu&layout=compact&theme=graywhite&bg_color=f7f1e3,ede0c0&title_color=3a2a1a&text_color=2c2c2c&border_color=c9b88a" alt="Top Languages" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=cubeyu&theme=graywhite&background=f7f1e3&stroke=c9b88a&ring=8b1a1a&fire=a83232&currStreakLabel=3a2a1a&sideNums=2c2c2c&currStreakNum=a83232&dates=5a4632" alt="Streak Stats" />
</p>

<br/>

<!-- ============ 鸿雁传书 ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNDAiIGhlaWdodD0iNDgiIHZpZXdCb3g9IjAgMCAyNDAgNDgiPjx0ZXh0IHg9IjEyMCIgeT0iMzIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiMzYTJhMWEiIGZvbnQtc2l6ZT0iMjgiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVFNvbmcsIFNpbVN1biwg5a6L5L2TLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiIGxldHRlci1zcGFjaW5nPSI2Ij7il4gg6bi/6ZuB5Lyg5LmmPC90ZXh0PjxsaW5lIHgxPSIyMCIgeTE9IjQyIiB4Mj0iMjIwIiB5Mj0iNDIiIHN0cm9rZT0iIzhiMWExYSIgc3Ryb2tlLXdpZHRoPSIxLjUiLz48L3N2Zz4=" width="240" height="48" alt="◈ 鸿雁传书" />
</div>

<p align="center">
  <a href="https://github.com/cubeyu">
    <img src="https://img.shields.io/badge/GitHub-墨客居所-1a1a1a?style=for-the-badge&logo=github&logoColor=f5f0e6&labelColor=a83232" alt="GitHub" />
  </a>
</p>

<p align="center">
  <a href="mailto:hello@techisle.top">
    <img src="https://img.shields.io/badge/Email-飞鸽传书-a83232?style=for-the-badge&logo=gmail&logoColor=f5f0e6&labelColor=1a1a1a" alt="Email" />
  </a>
</p>

<p align="center">山高水长，江湖再见 · 期待与你共话技术春秋</p>

<br/>

<!-- ============ 底部：墨竹 + 印章（Base64 SVG） ============ -->
<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0NDAiIGhlaWdodD0iMTIwIiB2aWV3Qm94PSIwIDAgNDQwIDEyMCI+CiAgPCEtLSDloqjnq7nnq78gLS0+CiAgPHBhdGggZD0iTTUwIDExNSBRIDUyIDY1IDU1IDIwIiBzdHJva2U9IiMxYTFhMWEiIHN0cm9rZS13aWR0aD0iMy41IiBmaWxsPSJub25lIiBvcGFjaXR5PSIwLjg1Ii8+CiAgPCEtLSDnq7noioIgLS0+CiAgPGNpcmNsZSBjeD0iNTIiIGN5PSI5NSIgcj0iMyIgZmlsbD0iIzFhMWExYSIgb3BhY2l0eT0iMC44NSIvPgogIDxjaXJjbGUgY3g9IjUzIiBjeT0iNjUiIHI9IjMiIGZpbGw9IiMxYTFhMWEiIG9wYWNpdHk9IjAuODUiLz4KICA8Y2lyY2xlIGN4PSI1NCIgY3k9IjM4IiByPSIzIiBmaWxsPSIjMWExYTFhIiBvcGFjaXR5PSIwLjg1Ii8+CiAgPCEtLSDnq7nlj7YgLS0+CiAgPHBhdGggZD0iTTU1IDMyIFEgNzggMjMgOTggMjkgUSA4MCAzNyA1NSAzMiBaIiBmaWxsPSIjMmMyYzJjIiBvcGFjaXR5PSIwLjgiLz4KICA8cGF0aCBkPSJNNTQgNTIgUSAzMCA0MCAxMCA0NiBRIDI2IDU0IDU0IDUyIFoiIGZpbGw9IiMxYTFhMWEiIG9wYWNpdHk9IjAuODUiLz4KICA8cGF0aCBkPSJNNTMgNzIgUSA3NSA2MiA5OCA2OCBRIDc5IDc2IDUzIDcyIFoiIGZpbGw9IiMyYzJjMmMiIG9wYWNpdHk9IjAuNzUiLz4KICA8cGF0aCBkPSJNNTUgMjQgUSA3NCAxMSA5NCAxNCBRIDc2IDI0IDU1IDI0IFoiIGZpbGw9IiMxYTFhMWEiIG9wYWNpdHk9IjAuOSIvPgogIDxwYXRoIGQ9Ik01NCA4OCBRIDMwIDc5IDEwIDg0IFEgMjYgOTIgNTQgODggWiIgZmlsbD0iIzJjMmMyYyIgb3BhY2l0eT0iMC43Ii8+CgogIDwhLS0g5Lit6Ze06aKY5a2XIC0tPgogIDx0ZXh0IHg9IjIyMCIgeT0iNjUiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiM1YTQ2MzIiIGZvbnQtc2l6ZT0iMjAiIGZvbnQtZmFtaWx5PSJTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBzZXJpZiIgbGV0dGVyLXNwYWNpbmc9IjYiPue6uOefreaDhemVvyDCtyDnoIHmtbfml6DlnqA8L3RleHQ+CgogIDwhLS0g5pyx56CC6JC95qy+5Y2w56ugIC0tPgogIDxyZWN0IHg9IjM1NSIgeT0iNTUiIHdpZHRoPSI1NSIgaGVpZ2h0PSI1NSIgZmlsbD0iI2E4MzIzMiIgcng9IjMiIG9wYWNpdHk9IjAuOTIiLz4KICA8dGV4dCB4PSIzODIuNSIgeT0iODAiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiNmNWYwZTYiIGZvbnQtc2l6ZT0iMTUiIGZvbnQtZmFtaWx5PSJTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBzZXJpZiIgZm9udC13ZWlnaHQ9ImJvbGQiPmN1YmV5dTwvdGV4dD4KICA8dGV4dCB4PSIzODIuNSIgeT0iMTAwIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSIjZjVmMGU2IiBmb250LXNpemU9IjEyIiBmb250LWZhbWxseT0iU1RGYW5nc29uZywgRmFuZ1NvbmcsIOS7v+Wuiywgc2VyaWYiPuWiqOWNsDwvdGV4dD4KPC9zdmc+Cg==" width="440" height="120" alt="墨竹落款" />
</div>

<div align="center">
  <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIzMjAiIGhlaWdodD0iMzAiIHZpZXdCb3g9IjAgMCAzMjAgMzAiPgogIDx0ZXh0IHg9IjE2MCIgeT0iMjIiIHRleHQtYW5jaG9yPSJtaWRkbGUiIGZpbGw9IiM4YjZmNDgiIGZvbnQtc2l6ZT0iMTMiIGZvbnQtZmFtaWx5PSJTVEZhbmdzb25nLCBGYW5nU29uZywg5Lu/5a6LLCBTVEthaXRpLCBLYWlUaSwg5qW35L2TLCBzZXJpZiIgZm9udC1zdHlsZT0iaXRhbGljIiBsZXR0ZXItc3BhY2luZz0iNiI+4oCUIGN1YmV5dSDliLYgwrcg5bKB5qyh5LiZ5Y2IIOKAlDwvdGV4dD4KPC9zdmc+Cg==" width="320" height="30" alt="— cubeyu 制 · 岁次丙午 —" />
</div>

<br/>

<!-- ============ 折叠区：设计说明 ============ -->
<details>
<summary>📜 关于本主页的设计说明（点击展开）</summary>

**GitHub HTML 限制真相**

GitHub 使用 `html-pipeline` + `sanitize` 库过滤 Markdown 中的 HTML：

- ❌ `<svg>`, `<path>`, `<text>` 不在元素白名单中，内联 SVG 会被**完全移除**
- ❌ `bgcolor`, `style`, `class` 属性不在白名单中，会被**移除**
- ❌ `<link>`, `<style>`, `<script>` 标签不在白名单中，会被**移除**
- ✅ `<img src="...">` 完全允许，包括 `data:` 协议

**本主页实现方案（v3.0.0）**

1. **古风文字**：所有标题文字都做成 SVG 图片 → Base64 → `<img>` 引用
   - SVG 内 `font-family` 走系统字体兜底链：STKaiti, KaiTi, 楷体, STFangsong, FangSong, 仿宋, STSong, SimSun, 宋体, serif
   - Windows 用户可见楷体/仿宋，macOS 用户可见华文楷体/华文仿宋，Linux 回退到 serif

2. **水墨装饰**：山水横幅、朱砂分割线、墨竹印章全部是 Base64 SVG 图片

3. **卡片分区**：用章节标题图片 + `<br/>` 营造分区感，不依赖背景色

4. **徽章**：Shields.io 动态生成，主题配色与古风一致

5. **统计图**：github-readme-stats + streak-stats，自定义配色匹配水墨主题

**完整效果预览**：查看同目录下的 [preview.html](preview.html)，加载 Google Fonts 古风字体，呈现理想效果。

</details>
