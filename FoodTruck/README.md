# 餐車搶班系統 (FoodTruck Slot Booking System)

一個公平、高效、可自動計算費用的餐車/攤商搶班平台，減少人工干預與爭議。本系統提供完整的場次管理、報名流程、規則引擎與帳務統計功能。

## 📋 專案簡介

傳統餐車/攤商的場地排班流程繁瑣，常需要人工統計與人工分配。本系統讓攤商能夠自行報名，並自動遵循各種規範（場地數量限制、前二後二限制、同日單場限制等），實現公平、高效的資源分配。

### 核心特色

- ⚡ **毫秒級排序**：依提交時間毫秒級排序進行核配，確保公平性
- 🛡️ **智能規則引擎**：自動檢查單日限制、場次限制、前二後二規範、品類衝突等
- 📊 **完整帳務系統**：自動計算費用、生成對帳單、支援匯出功能
- 🔐 **安全認證**：基於 Redis Session 的現代化認證系統，支援 Rate Limiting、帳號鎖定
- 📅 **場次管理**：支援批次建立、行事曆檢視、預留名額等功能
- 🎨 **現代化 UI**：採用 shadcn/ui + Radix UI，響應式設計，支援深色模式

## 🛠️ 技術棧

### 前端框架
- **Next.js 15** - App Router 架構，支援 Server Components 與 Client Components
- **React 19** - 最新版本的 React，支援 Server Components
- **TypeScript** - 完整的型別安全
- **Tailwind CSS 4.0** - 現代化 CSS 框架，支援 JIT 編譯

### UI 組件庫
- **shadcn/ui** - 基於 Radix UI 的組件系統
- **Radix UI** - 無障礙的 UI 元件庫（Dialog、Dropdown、Select、Tabs 等）
- **Lucide React** - 現代化圖示庫
- **Remix Icon** / **Tabler Icons** - 額外圖示支援

### 表單與驗證
- **React Hook Form** - 高效能表單管理
- **Zod** - Schema 驗證與型別推斷
- **@hookform/resolvers** - React Hook Form 與 Zod 整合

### 資料庫與後端
- **Supabase** - PostgreSQL 資料庫
  - **Supabase Auth** - 使用者認證（支援 Email/Password、Google OAuth）
  - **Row Level Security (RLS)** - 資料庫層級的安全控制
  - **PostgreSQL Functions (RPC)** - 資料庫函數與觸發器
- **Upstash Redis** - Session 管理、Rate Limiting、Token Blacklist

### 狀態管理與資料獲取
- **Server Components** - Next.js 15 的伺服器端元件
- **Server Actions** - 伺服器端動作處理
- **React Query** - 客戶端資料快取

### 工具庫
- **date-fns** - 日期處理與格式化
- **react-day-picker** - 日期選擇器
- **@dnd-kit** - 拖放功能（排序、拖曳）
- **@tanstack/react-table** - 資料表格
- **recharts** - 圖表繪製
- **html2canvas** - 截圖功能（對帳單匯出）
- **sonner** - Toast 通知
- **next-themes** - 深色模式支援
- **class-variance-authority** - 條件式樣式管理
- **clsx** / **tailwind-merge** - 樣式合併工具

### 開發工具
- **ESLint** - 程式碼檢查
- **TypeScript** - 型別檢查
- **Turbopack** - 快速開發建置工具
- **PostCSS** / **Autoprefixer** - CSS 處理

### 部署與監控
- **Vercel** - 部署平台
- **GitHub Actions** - CI/CD 流程

## 🎯 主要功能

### 攤商功能

#### 註冊與認證
- 攤商註冊（需管理員審核）
- Email/Password 登入
- Google OAuth 登入
- 忘記密碼功能
- Remember Me 功能
- 多裝置 Session 管理

#### 個人資料管理
- 查看與編輯個人資料
- 商品類別設定（大品類、小品類、品項）
- 聯絡資訊更新
- 密碼修改

#### 場次瀏覽與報名
- 月曆檢視可報名場次
- 場次詳細資訊（地點、日期、費用、剩餘名額）
- 即時搶班申請
- 申請狀態即時回饋（成功/失敗）
- 查看剩餘可報名名額

#### 申請管理
- 查看我的報名清單
- 申請狀態查詢（pending、approved、rejected、canceled）
- 申請歷史記錄
- 待審核狀態提醒

#### 帳務查詢
- 查看應繳費用彙總
- 對帳單查詢與匯出
- 費用明細查看

### 管理員功能

#### 儀表板
- 系統統計概覽
- 場次狀態統計
- 報名趨勢圖表
- 快速操作入口

#### 場次管理
- 新增/編輯場次（地點、日期、攤位數量、費用）
- 批次建立場次（依日期範圍、依地點）
- 場次行事曆檢視
- 場次狀態管理（draft、open、closed、completed）
- 預留名額設定
- 場次類型限制（餐車/落地攤）
- 搶班時間窗口設定

#### 報名管理
- 報名清單查看與篩選
- 申請審核（approve/reject）
- 申請取消（含原因記錄）
- 報名統計報表
- 失敗原因分析

#### 攤商管理
- 攤商註冊審核
- 攤商資料查詢與編輯
- 攤商狀態管理（pending、active、suspended）
- 攤商搜尋與篩選
- 商品類別管理

#### 地點與地區管理
- 地區管理（新增/編輯/刪除）
- 地點管理（名稱、地址、最大容納數、屬性）
- 地點搜尋與篩選

#### 商品類別管理
- 商品類別 CRUD（大品類/小品類）
- 類別層級設定
- 類別提示（hint）維護
- 小品類互斥群組設定

#### 帳務管理
- 對帳單查詢與篩選
- 對帳單生成（單一攤商/批次）
- 對帳單匯出（Excel/CSV）
- 對帳單狀態管理（draft、finalized、voided）
- 費用統計報表

#### 使用者管理
- 使用者清單查看
- 使用者角色管理
- 使用者搜尋

#### 系統設定與安全
- 系統健康檢查
- Session 管理（查看、登出特定裝置）
- 帳號鎖定管理
- 異常行為偵測記錄
- Rate Limiting 監控

## 🔒 系統規則

### 報名規則引擎
- **單日限制**：同一攤商一天只能報名一個地點
- **場次限制**：一場次不可重複報名（資料層 unique 保證）
- **先後順序**：依提交時間毫秒級排序進行核配
- **前二後二限制**：
  - 僅同一地點需檢查，跨地點不影響
  - 同日同場次：只要大品類相同 → 衝突
  - 以場次日期為中心，往前兩天與往後兩天為檢查範圍：
    - 大品類 + 小品類相同 → 衝突
    - 大品類相同但小品類不同 → 不衝突
    - 大品類不同 → 不衝突
    - 同小品類且「品項」相同 → 一律衝突
- **品類互斥**：管理員可設定小品類互斥群組，同群組內不可同時報名
- **候補機制**：不提供，由管理員手動調整
- **取消規則**：攤商不可自行取消，僅管理員手動取消並記錄原因

### 安全機制
- **Rate Limiting**：防止暴力破解與濫用
- **帳號鎖定**：多次失敗登入後自動鎖定
- **Token Blacklist**：登出後 Token 立即失效
- **Session 管理**：支援多裝置管理，可遠端登出
- **異常行為偵測**：記錄可疑操作行為

## 🚀 快速開始（Windows / PowerShell）

### 前置需求
- Node.js >= 18.0.0
- npm 或 yarn
- Supabase 專案（用於資料庫與認證）
- Upstash Redis 專案（用於 Session 管理，可選）

### 安裝步驟

1. **安裝依賴**
```powershell
cd web
npm install
```

2. **建立環境變數**
```powershell
Copy-Item .env.example .env.development.local
# 依需求再建立 .env.staging.local、.env.production.local 並填入
```

3. **設定環境變數**
編輯 `.env.development.local`，填入以下變數：
```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key
UPSTASH_REDIS_REST_URL=your_redis_url 
UPSTASH_REDIS_REST_TOKEN=your_redis_token 
```

4. **執行資料庫遷移**
```powershell
# 在 Supabase Dashboard 執行 db/migrations/ 目錄下的 SQL 檔案
```

5. **啟動開發伺服器**
```powershell
npm run dev
```

應用程式將在 `http://localhost:3001` 啟動。

## 📦 環境變數說明

### 必要變數
- `NEXT_PUBLIC_SUPABASE_URL` - Supabase 專案 URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` - Supabase 匿名金鑰（公開）
- `SUPABASE_SERVICE_ROLE_KEY` - Supabase 服務角色金鑰（僅伺服器端，需保密）

### 可選變數
- `UPSTASH_REDIS_REST_URL` - Upstash Redis REST API URL（Session 管理）
- `UPSTASH_REDIS_REST_TOKEN` - Upstash Redis REST API Token

## 🔄 CI/CD

### GitHub Actions
- **工作流程**：`.github/workflows/ci.yml`
- **流程步驟**：
  1. Install - 安裝依賴
  2. Lint - 程式碼檢查
  3. Build - 建置專案
- **環境變數**：需於 Repo Secrets 設定與環境變數同名的鍵值

## 📚 專案文件

### 需求與規格文件
- **PRD**：`others/餐車搶班系統_PRD.md` - 產品需求文件
- **ERD**：`others/ERD.md` - 資料庫實體關係圖
- **Spec**：`others/Spec.md` - 系統規格文件
- **Plan**：`others/Plan.md` - 實作計畫

### 操作手冊
- **攤商搶班流程手冊**：`doc/攤商搶班流程手冊.md`
- **攤商個人資料管理手冊**：`doc/攤商個人資料管理手冊.md`
- **管理員場次管理手冊**：`doc/管理員場次管理手冊.md`
- **管理員攤商管理手冊**：`doc/管理員攤商管理手冊.md`
- **管理員申請審核手冊**：`doc/管理員申請審核手冊.md`
- **管理員帳務管理手冊**：`doc/管理員帳務管理手冊.md`
- **管理員系統設定手冊**：`doc/管理員系統設定手冊.md`
- **系統規則說明手冊**：`doc/系統規則說明手冊.md`
- **故障排除指南**：`doc/故障排除指南.md`

### 技術文件
- **專案總結**：`web/docs/Guide/PROJECT_SUMMARY.md`
- **Session 管理技術文件**：`web/docs/Session管理技術文件.md`

## 📁 專案結構

```
FoodTruckSlotBookingSystem/
├── web/                    # Next.js 前端應用
│   ├── src/
│   │   ├── app/            # App Router 路由
│   │   │   ├── admin/      # 管理員後台
│   │   │   ├── api/        # API 路由
│   │   │   ├── dashboard/  # 攤商儀表板
│   │   │   ├── me/         # 個人中心
│   │   │   └── sessions/   # 場次頁面
│   │   ├── components/     # React 組件
│   │   ├── lib/            # 工具函數
│   │   └── types/          # TypeScript 型別定義
│   └── docs/               # 文件
├── db/                     # 資料庫相關
│   ├── migrations/         # 資料庫遷移檔案
│   ├── seeds/              # 種子資料
│   └── scripts/            # 資料庫腳本
├── doc/                    # 操作手冊
├── others/                 # 需求與規格文件
└── .github/                # GitHub Actions 工作流程
```

## 🤝 開發規範

詳細的開發規範請參考 `CONTRIBUTING.md`。

