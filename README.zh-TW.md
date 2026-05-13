# Guizang PPT Skill · 網頁 PPT / 配圖 / 封面

> 🌏 **English: [README.en.md](./README.en.md)** · **简体中文: [README.md](./README.md)**

一個適配 Claude Code / Codex 等 Agent 環境的網頁 PPT 技能,用於生成**單檔案 HTML 橫向翻頁 PPT**、PPT 配圖和多平臺封面。

內置兩套視覺系統:

- **Style A: 電子雜誌 × 電子墨水**。像 *Monocle* 貼上了代碼,適合敘事、觀點、分享、個人風格表達。
- **Style B: 瑞士國際主義**。網格至上、單一高飽和錨點色、直角、髮絲線、極致字號對比,適合事實、產品、分析、方法論表達。

> 由 [歸藏](https://x.com/op7418) 在"一人公司:被 AI 摺疊的組織"、"一種新的工作方式"等線下分享中沉澱而成,踩過的每一個坑都寫進了 `checklist.md`。

**舊主題 · Style A 電子雜誌風**

![Style A 電子雜誌風效果展示](https://github.com/user-attachments/assets/5dc316a2-401c-4e37-9123-ea081b6ae470)

**新主題 · Style B 瑞士國際主義**

![Style B 瑞士國際主義效果展示](https://github.com/user-attachments/assets/8960e78c-69bb-4b7e-aa95-6fad64b70314)

## 效果

- 🖋 **雙視覺系統**:電子雜誌風負責敘事,瑞士風負責事實表達
- 📐 **橫向左右翻頁**:鍵盤 ← → / 滾輪 / 觸屏滑動 / 底部圓點 / ESC 索引
- 🧩 **Style A 10 種布局**:封面、章節、數據大字報、圖文、圖片網格、Pipeline、對比等
- 🧱 **Style B 22 種鎖定版式**:Cover、Statement、KPI Tower、Loop Diagram、Duo Compare、Image Hero、Closing Manifesto 等
- 🎨 **主題色預設**:Style A 5 套電子墨水主題,Style B 4 套瑞士高飽和錨點色
- 🖼 **Codex 可選配圖流程**:可用 GPT-Image 2.0 / GPT-M 2.0 生成紀實照片、資訊圖表、流程圖、系統關係圖、UI 情景圖,並按模板比例插入
- 📰 **多平臺封面**:可用同一套視覺規則生成公眾號 21:9、公眾號分享卡 1:1、小紅書 3:4、視頻號橫版等封面
- 📴 **低性能靜態模式**:按 `B` 可關閉 WebGL / canvas 動畫,讓動態內容退回靜態背景
- 🌏 **繁簡雙字體**:預設繁體中文(TC)字型,Agent 偵測到簡體輸入自動切換為 SC 字型
- 📄 **單檔案 HTML**:不需要構建、不需要伺服器,瀏覽器直接打開

## 適合 / 不適合

**✅ 合適**:線下分享 / 行業內部講話 / 私享會 / AI 產品發布 / demo day / 帶強烈個人風格的演講

**❌ 不合適**:大段表格數據 / 培訓課件(資訊密度不夠)/ 需要多人協作編輯(靜態 HTML)

## 安裝

### 方式一:一行命令安裝(推薦)

```bash
npx skills add https://github.com/alingowangxr/guizang-ppt-skill --skill guizang-ppt-skill
```

### 方式二:把下面這段話直接發給 AI

> 幫我安裝 `guizang-ppt-skill` 這個 Claude Code skill。請按下面步驟做:
>
> 1. 確保 `~/.claude/skills/` 目錄存在(不存在就創建)
> 2. 執行 `git clone https://github.com/alingowangxr/guizang-ppt-skill.git ~/.claude/skills/guizang-ppt-skill`
> 3. 驗證:`ls ~/.claude/skills/guizang-ppt-skill/` 應該看到 `SKILL.md`、`assets/`、`references/` 三項
> 4. 告訴我安裝好了,之後我說"做一份雜誌風 PPT"之類的話就會觸發這個 skill

把這段話複製貼上給 Claude Code / Cursor / 任何有 shell 權限的 AI Agent,它會自動完成安裝。

### 方式三:手動命令行

```bash
git clone https://github.com/alingowangxr/guizang-ppt-skill.git ~/.claude/skills/guizang-ppt-skill
```

## 繁簡中文支援

模板內建繁簡雙字體支援。**預設繁體中文(TC)**，載入 Noto Sans/Serif TC 及系統對應字型(PingFang TC / Microsoft JhengHei)。若輸入為簡體中文，Agent 會自動在 `<html>` 上加 `class="sc"` 並改 `lang="zh-CN"`，切換為 SC 字型(Noto Sans/Serif SC / PingFang SC / Microsoft YaHei)。

兩種風格(Style A/B)的模板均支援此機制。

### 觸發方式

裝好後,Claude Code 會在對話裡自動發現並調用這個 skill。觸發關鍵詞:

- "幫我做一份雜誌風 PPT"
- "幫我做一份瑞士風 PPT"
- "生成一個 horizontal swipe deck"
- "editorial magazine style presentation"
- "electronic ink 風格演講 slides"
- "基於這篇文章做一張公眾號 21:9 封面"
- "基於這份 PPT 生成一張 1:1 分享卡"
- "幫我生成一張 Facebook 1.91:1 封面"
- "做一張 Instagram 直式 Reels 封面"
- "幫我把這篇文章做成 LINE 官方帳號封面"
- "生成 YouTube 縮圖"
- "幫我生成 LinkedIn 橫幅"

## 使用流程

Skill 本身是結構化工作流,Agent 會逐步引導:

1. **選擇風格** — Style A 電子雜誌風,或 Style B 瑞士國際主義
2. **需求澄清** — 6 問清單:受眾、時長、素材、圖片、主題色、硬約束
3. **拷貝模板** — Style A 用 `assets/template.html`,Style B 用 `assets/template-swiss.html`
4. **填充內容** — 先做主題節奏表,再從對應 layout 骨架裡挑、貼、改文案
5. **可選配圖** — 在 Codex 中詢問是否用 GPT-Image 2.0 / GPT-M 2.0 生成配圖,再按頁面比例插入
6. **自檢** — 對照 `references/checklist.md`,P0 級問題必須全過；瑞士風還要運行版式校驗器
7. **預覽** — 瀏覽器直接打開
8. **迭代** — inline style 改字號/高度/間距

詳細說明見 [`SKILL.md`](./SKILL.md)。

## Style B 瑞士風

瑞士風是這次新增的結構化主題。它不是"換一套 CSS",而是一套更嚴格的版式系統。

- **22 個具名版式**:正文頁只能從 `S01` 到 `S22` 中選擇,不能臨時發明頁面結構
- **4 套錨點色**:克萊因藍 IKB、檸檬黃、檸檬綠、安全橙
- **網格鎖定**:16 列 grid、直角色塊、1px 髮絲線、無陰影、無漸變、無圓角
- **中文字號收斂**:全中文大標題需要降一檔,避免佔掉正文和圖片空間
- **圖文底對齊**:左文右圖 / 左圖右文場景優先讓正文塊與圖片底部對齊,同時避開頁腳翻頁組件
- **圖片槽位綁定**:圖片必須進入模板預留的 `data-image-slot`,常見主圖按 21:9 或 16:10 生成
- **強校驗**:用腳本攔住居中標題、實驗版式、SVG 內寫字、圖片脫離槽位等問題

瑞士風校驗命令:

```bash
node scripts/validate-swiss-deck.mjs path/to/index.html
```

## Codex 配圖能力

在 Codex 環境中,完成 deck 初稿後可以主動詢問用戶是否需要生成配圖。用戶確認後,再詢問圖片類型或風格,常用類型包括:

- 人文紀實照片:富士 / 徠卡感的真實場景,增加人文表現力
- 資訊圖表 / 流程圖 / 對比圖 / 系統關係圖:用於解釋無法用實拍照片說明的概念
- 截圖再設計 / UI 情景圖:把原始截圖統一成適合 PPT 的比例和視覺密度
- 數據大字報 / 數據圖表:把關鍵數字做成可直接插入 PPT 的視覺素材
- 多圖拼貼:用於極寬圖片槽位,避免把三張 16:9 圖片硬塞進三列

生成圖片時要遵守三個關鍵規則:

- 圖片是 PPT 中的嵌入素材,不要自帶頁腳、頁底、標題、角標、頁碼或裝飾邊框
- 圖片語言跟隨 deck 語言:中文 deck 的資訊圖表用中文標籤,英文 deck 用英文標籤
- 圖片比例必須先匹配落位:瑞士風主圖常用 21:9,通用主圖常用 16:9 / 16:10,截圖再設計常用 16:10,多圖網格統一高度

配圖提示詞見 [`references/image-prompts.md`](./references/image-prompts.md)。

## 封面生成

這個 Skill 也可以基於文章或 PPT 核心觀點生成平臺封面。以下是在臺灣常用平臺的建議規格:

| 平臺 | 比例 | 建議 |
|------|------|------|
| **Facebook 粉絲專頁 / 社團** | 1.91:1 | 封面橫幅、貼文配圖，大標題置左或置中 |
| **Facebook 貼文 / 分享卡** | 1:1 | 乾淨大字 + 一個視覺錨點，適合被動態牆裁切 |
| **Instagram 貼文** | 1:1 | 正方形，圖文整合，字號要大 |
| **Instagram 直式 / Reels** | 9:16 | 滿版直式，大標題 + 強烈視覺焦點 |
| **Instagram 輪播** | 4:5 | 多張時統一字號、色調和視覺節奏 |
| **YouTube 縮圖** | 16:9 | 標題 + 副標題 + 單一視覺焦點，字要大 |
| **LINE 官方帳號封面** | 16:9 | 品牌主色 + 一句話定位，避免資訊過多 |
| **LINE VOOM / 貼文** | 1:1 | 短影音或圖文封面，類似 IG 正方形 |
| **LinkedIn 橫幅** | 4:1 | 極寬版，主標題 + 職稱 / 品牌名 |
| **LinkedIn 貼文配圖** | 1.91:1 | 文章或觀點分享，標題 + 摘要感 |

> 若需要中國平臺(微信公眾號 21:9、小紅書 3:4、視頻號 16:9 等)，Agent 會自動根據輸入情境判斷輸出。

封面原則和 PPT 一樣:只用少量關鍵詞,視覺重心落在大標題上,不要把正文堆滿。

## 目錄結構

```
guizang-ppt-skill/
├── SKILL.md              ← Skill 主文件:工作流、原則、常見錯誤
├── README.md             ← 簡體中文版
├── README.en.md          ← 英文版
├── README.zh-TW.md       ← 本文件(繁體中文版)
├── assets/
│   ├── template.html         ← Style A 電子雜誌風模板
│   └── template-swiss.html   ← Style B 瑞士國際主義模板
├── scripts/
│   └── validate-swiss-deck.mjs ← 瑞士風版式校驗器
└── references/
    ├── components.md     ← 組件手冊(字體、色、網格、圖標、callout、stat、pipeline)
    ├── layouts.md        ← 10 種頁面布局骨架(可直接貼上)
    ├── layouts-swiss.md  ← 22 種瑞士風鎖定版式
    ├── swiss-layout-lock.md ← 瑞士風還原度和版式硬約束
    ├── themes.md         ← 5 套主題色預設(只能選不能自定義)
    ├── themes-swiss.md   ← 4 套瑞士風錨點色
    ├── image-prompts.md  ← GPT-Image 2.0 / GPT-M 2.0 配圖類型、比例和基礎提示詞
    └── checklist.md      ← 質量檢查清單(P0 / P1 / P2 / P3 分級)
```

## 主題色預設

從 `references/themes.md` 裡選一套——**不允許自定義 hex 值**,保護美學比給自由更重要。

| 主題 | 適合場景 |
|------|---------|
| 🖋 墨水經典 | 通用預設、商業發布、不知道選啥 |
| 🌊 靛藍瓷 | 科技 / 研究 / AI / 技術發布會 |
| 🌿 森林墨 | 自然 / 可持續 / 文化 / 非虛構 |
| 🍂 牛皮紙 | 懷舊 / 人文 / 文學 / 獨立雜誌 |
| 🌙 沙丘 | 藝術 / 設計 / 創意 / 畫廊 |

切換主題只需替換 `template.html` 開頭 `:root{}` 裡的 6 行變量,其他 CSS 全走 `var(--...)`。

### Style B 瑞士主題

瑞士風從 `references/themes-swiss.md` 裡選一套,同樣**不允許自定義 hex 值**。

| 主題 | 適合場景 |
|------|---------|
| 克萊因藍 IKB | 通用預設、商業發布、AI 產品、方法論 |
| 檸檬黃 | 年輕、運動、零售、Y2K 復古 |
| 檸檬綠 | 生態、可持續、Z 世代品牌 |
| 安全橙 | 警示、新聞、活力主題 |

如果用戶說"瑞士風 PPT"但沒有指定顏色,預設推薦克萊因藍 IKB。

## 核心設計原則

1. **克制優於炫技** — WebGL 背景只在 hero 頁透出
2. **結構優於裝飾** — 資訊靠字號 + 字體對比 + 網格留白,不用陰影和浮動卡片
3. **圖片是第一公民** — 圖片要對齊正文內容區,比例穩定,只裁底部,頂部和左右完整
4. **配圖只做素材** — 生成圖只保留核心照片 / 圖表 / UI,不要把 PPT 頁腳、標題和角標畫進圖片裡
5. **節奏靠 hero 頁** — hero / non-hero 交替,才不累眼睛
6. **低性能可退場** — 按 `B` 能切換到靜態模式,動態效果不能成為閱讀負擔
7. **術語統一** — Skills 就是 Skills,不中英混譯
8. **瑞士風必須守版式** — Style B 優先還原原始 22P 版式,不要為了"多樣"發明不存在的頁面

## 視覺參考

- [*Monocle*](https://monocle.com) 雜誌的版式
- YC Garry Tan "Thin Harness, Fat Skills"
- Massimo Vignelli / Helvetica Forever / 瑞士國際主義網格系統
- 歸藏線下分享 PPT 系列

## 貢獻

Bug、排版問題、新布局需求——歡迎開 Issue 或 PR。改動請優先:

- 在 `template.html` 裡補類,不要讓 layouts.md 使用未定義的類
- 在 `template-swiss.html` 裡補類時,同步更新 `layouts-swiss.md` 和 `swiss-layout-lock.md`
- 瑞士風新增規則後,同步更新 `scripts/validate-swiss-deck.mjs`
- 把踩過的坑寫到 `checklist.md` 對應的 P0 / P1 / P2 / P3 級別
- 新主題色進 `themes.md` 並給出適合的場景

## License

MIT © 2026 [op7418](https://github.com/op7418)

