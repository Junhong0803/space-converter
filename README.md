# 空白換行轉換器 · dreamhomes.com.tw

仿 tool.lifehacker.tw/space-converter 做的同功能工具，掛你自己的品牌。

## 怎麼打開

直接雙擊 `index.html` 或在終端機：

```bash
open "/Users/chenjunhong/Downloads/Hong - 智能/100_Todo/projects/space-converter/index.html"
```

不用裝任何東西，純前端 HTML + Tailwind CDN，瀏覽器直接開就能用。

## 功能

- 貼上原文 → 按「一鍵轉換」→ 一鍵複製
- 自動在空行插入零寬度空白（U+200B），IG / Threads / FB 的空行就不會被吃掉
- 進階選項：每行末尾加、開頭加（對付頑固的平台）
- 即時字元計數

## 換 LOGO 的兩個方法

**A. 用圖檔**（最快）

把你的 LOGO 存成 `assets/logo.svg`（或 logo.png 同時改 HTML 裡的 `src="assets/logo.svg"` → `src="assets/logo.png"`）。
我在 HTML 裡留了 `onerror` fallback — 如果圖檔掛了會自動顯示文字 logo「D」。

**B. 只改文字**

打開 `index.html`，搜尋 `dreamhomes.com.tw` 改成你要的名字，搜尋 `俊宏的房地產筆記` 改成你要的 tagline。

## 改配色

`index.html` 開頭有一段 `tailwind.config`，改 `brand` 顏色即可：

```js
colors: {
  brand: {
    500: '#3b5bd9',  // 主色（按鈕、強調）
    600: '#2c48c0',  // hover
    // ...
  },
},
```

改完存檔、瀏覽器重新整理就看到效果。

## 技術細節

- 單檔 HTML，沒有 build、沒有 Node 依賴
- 零寬度空白字元：`​`（U+200B ZERO WIDTH SPACE）
- 使用 `navigator.clipboard.writeText` 複製，舊瀏覽器 fallback 用 `document.execCommand('copy')`
- 字型：Noto Sans TC（Google Fonts CDN）

## 之後要上線

想上線給別人用時，最快的路徑：

1. **GitHub Pages**：推到一個新 repo → Settings → Pages → Deploy from main
2. **Zeabur**：直接拖資料夾上去，秒開
3. **Cloudflare Pages / Vercel**：同樣拖即上線

都是免費的，挑一個就好。
