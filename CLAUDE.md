# CLAUDE.md - topsteps_code 專案的 AI 助理指南

**最後更新：** 2025-11-20
**專案擁有者：** CIOU,GUO-YU (zxcvbn1294)
**授權：** MIT
**建立日期：** 2025 年 10 月 8 日

---

## 目錄

1. [專案概覽](#專案概覽)
2. [目前專案狀態](#目前專案狀態)
3. [專案結構](#專案結構)
4. [Git 工作流程與分支策略](#git-工作流程與分支策略)
5. [開發指南](#開發指南)
6. [程式碼規範](#程式碼規範)
7. [測試策略](#測試策略)
8. [文件標準](#文件標準)
9. [AI 助理工作流程](#ai-助理工作流程)
10. [未來開發藍圖](#未來開發藍圖)

---

## 專案概覽

### 目的
這是 **topsteps_code** 專案的起始儲存庫。此儲存庫於 2025 年 10 月初始化，目前處於早期階段。

### 儲存庫資訊
- **GitHub 網址：** https://github.com/zxcvbn1294/topsteps_code
- **主要語言：** 待定（目前尚無原始碼）
- **授權：** MIT License（版權所有 2025 CIOU,GUO-YU）
- **開發工具：** 整合 Claude Code

### 主要相關人員
- **擁有者/作者：** CIOU,GUO-YU (jack chiou)
- **AI 助理：** Claude (Anthropic)

---

## 目前專案狀態

### 狀態：**初始設定階段**

截至 2025 年 11 月，此儲存庫包含：
- ✅ MIT License 檔案
- ✅ 已初始化 Git 儲存庫
- ✅ 測試檔案（`test.txt`）用於工作流程驗證
- ❌ 無原始碼
- ❌ 無套件管理器設定
- ❌ 無建置工具
- ❌ 無測試框架
- ❌ 無文件（README.md）

### 提交歷史
```
b2a5f2c - Merge branch 'main' (2025年10月8日)
dd42544 - 新增測試檔案 (2025年10月8日) - 與 Claude 協作
04cd5c0 - Initial commit (2025年10月8日)
```

提交訊息「新增測試檔案」表明此專案由中文開發者維護，文件將以中文撰寫以提供更好的可讀性。

---

## 專案結構

### 目前結構
```
topsteps_code/
├── LICENSE              # MIT 授權檔案
├── test.txt            # Git 工作流程測試檔案
├── CLAUDE.md           # 本檔案 - AI 助理指南
└── .git/               # Git 元資料
```

### 建議的未來結構

當開始開發時，建議按照以下方式組織專案：

```
topsteps_code/
├── .github/            # GitHub 工作流程和模板
│   ├── workflows/      # CI/CD 管線
│   └── ISSUE_TEMPLATE/ # Issue 模板
├── docs/               # 專案文件
│   ├── api/           # API 文件
│   ├── guides/        # 使用指南
│   └── architecture/  # 架構決策
├── src/               # 原始碼
│   ├── components/    # 可重用元件（如適用）
│   ├── utils/         # 工具函式
│   ├── services/      # 商業邏輯/服務
│   └── config/        # 設定檔案
├── tests/             # 測試檔案
│   ├── unit/          # 單元測試
│   ├── integration/   # 整合測試
│   └── e2e/           # 端對端測試
├── scripts/           # 建置和部署腳本
├── .gitignore         # Git 忽略規則
├── package.json       # 依賴項（如果是 Node.js）
├── README.md          # 專案概述
├── CLAUDE.md          # 本檔案
├── CONTRIBUTING.md    # 貢獻指南
├── CHANGELOG.md       # 版本歷史
└── LICENSE            # MIT 授權
```

---

## Git 工作流程與分支策略

### 分支命名慣例

#### Claude Code 分支（AI 開發）
- **格式：** `claude/claude-md-<session-id>`
- **範例：** `claude/claude-md-mi7ev5g5uprc67u8-01GbonEGEV3zCN58trxhTCV5`
- **重要：** 所有 AI 助理分支必須以 `claude/` 前綴開頭
- **注意：** 推送到命名不正確的分支將會失敗並返回 403 錯誤

#### 人類開發者分支
- **功能分支：** `feature/<功能名稱>`
- **錯誤修復：** `fix/<錯誤描述>`
- **熱修復：** `hotfix/<issue-編號>`
- **實驗性：** `experiment/<實驗名稱>`

### 分支策略

1. **主分支：** `main`（受保護）
   - 僅包含可用於生產環境的程式碼
   - 需要 pull request 審查
   - 所有提交必須通過 CI/CD 檢查

2. **開發分支：** 各種功能/修復分支
   - 針對特定變更的短期分支
   - 透過 pull request 合併
   - 成功合併後刪除

3. **Claude 分支：** `claude/*`
   - AI 輔助開發會話
   - 每個會話建立唯一的 session ID
   - 必須使用 `-u origin <branch-name>` 推送

### Git 指令

#### AI 助理（Claude）使用
```bash
# 推送變更（重要：使用 -u 旗標）
git push -u origin claude/claude-md-<session-id>

# 網路錯誤處理：最多重試 4 次，採用指數退避
# 重試延遲：2秒、4秒、8秒、16秒

# 取得特定分支
git fetch origin <branch-name>

# 拉取變更
git pull origin <branch-name>
```

#### 提交訊息格式
```
<類型>: <主題>

<內容>

<頁尾>
```

**類型：**
- `feat`: 新功能
- `fix`: 錯誤修復
- `docs`: 文件變更
- `style`: 程式碼風格變更（格式化，無邏輯變更）
- `refactor`: 程式碼重構
- `test`: 新增或更新測試
- `chore`: 維護任務

**範例：**
```
feat: 新增使用者驗證模組

實作基於 JWT 的驗證機制，包含更新令牌功能。
新增登入、登出和令牌更新端點。

Co-authored-by: Claude <noreply@anthropic.com>
```

---

## 開發指南

### 開始開發前

1. **確定專案類型**
   - 網頁應用程式（前端/後端/全端）
   - 函式庫/套件
   - CLI 工具
   - API 服務
   - 行動應用程式
   - 桌面應用程式

2. **選擇技術堆疊**
   - 程式語言
   - 框架
   - 資料庫
   - 建置工具
   - 測試框架

3. **設定專案配置**
   - 初始化套件管理器（npm、pip、cargo 等）
   - 設定 linter 和格式化工具
   - 設定 pre-commit hooks
   - 建立 .gitignore 檔案

4. **建立初始文件**
   - 包含專案概述的 README.md
   - 供貢獻者使用的 CONTRIBUTING.md
   - 行為準則（選用）

### 安全最佳實踐

⚠️ **重要安全提醒：**
- 絕不提交機密資訊、API 金鑰或憑證
- 使用環境變數存放敏感設定
- 實作輸入驗證以防止注入攻擊
- 遵循 OWASP Top 10 指南
- 清理使用者輸入以防止 XSS
- 使用參數化查詢以防止 SQL 注入
- 實作適當的身分驗證和授權
- 保持依賴項更新以修補安全漏洞

### 程式碼品質標準

- **Linting：** 設定並強制執行程式碼檢查
- **格式化：** 使用一致的程式碼格式（Prettier、Black、rustfmt 等）
- **型別安全：** 適當使用 TypeScript、型別提示或靜態分析
- **程式碼審查：** 所有變更應透過 pull request 進行審查
- **文件：** 記錄公開 API、複雜邏輯和架構決策

---

## 程式碼規範

### 一般原則

1. **可讀性優先：** 程式碼應該自我說明
2. **DRY 原則：** 不要重複自己（Don't Repeat Yourself）
3. **SOLID 原則：** 遵循物件導向設計原則
4. **KISS：** 保持簡單（Keep It Simple, Stupid）
5. **YAGNI：** 你不會需要它（You Aren't Gonna Need It）（避免過度設計）

### 命名慣例

#### 變數和函式
```
camelCase      - JavaScript/TypeScript 變數和函式
snake_case     - Python 變數和函式
PascalCase     - 類別、介面、型別
SCREAMING_CASE - 常數
kebab-case     - 檔案名稱、URLs
```

#### 檔案和目錄
- 使用描述性的小寫名稱
- 使用連字號或底線分隔單字（保持一致）
- 元件檔案應與元件名稱相符

### 註解和文件

```javascript
/**
 * 函式的簡短描述
 *
 * @param {Type} paramName - 參數描述
 * @returns {Type} 返回值描述
 * @throws {ErrorType} 拋出錯誤的時機描述
 *
 * @example
 * functionName(arg1, arg2);
 */
function functionName(paramName) {
  // 實作
}
```

### 錯誤處理

- 始終明確處理錯誤
- 適當使用 try-catch 區塊
- 記錄錯誤時提供足夠的上下文
- 返回有意義的錯誤訊息
- 不要向終端使用者暴露內部錯誤細節

---

## 測試策略

### 測試金字塔

1. **單元測試（70%）**
   - 測試個別函式和方法
   - 快速、隔離、確定性
   - 模擬外部依賴

2. **整合測試（20%）**
   - 測試元件之間的互動
   - 驗證資料流和 API 契約

3. **端對端測試（10%）**
   - 測試完整的使用者工作流程
   - 從使用者角度驗證系統行為

### 測試組織

```
tests/
├── unit/
│   ├── utils.test.js
│   └── services.test.js
├── integration/
│   └── api.test.js
├── e2e/
│   └── user-flow.test.js
└── fixtures/
    └── test-data.json
```

### 測試命名慣例

```javascript
describe('ComponentName', () => {
  describe('methodName', () => {
    it('should do something when condition is met', () => {
      // Arrange（準備）
      // Act（執行）
      // Assert（斷言）
    });
  });
});
```

### 程式碼覆蓋率目標

- **最低：** 80% 整體覆蓋率
- **關鍵路徑：** 100% 覆蓋率
- **新程式碼：** 不應降低整體覆蓋率

---

## 文件標準

### README.md 結構

```markdown
# 專案名稱

簡短描述（1-2 句話）

## 功能
- 功能 1
- 功能 2

## 安裝
逐步安裝說明

## 使用方式
程式碼範例和使用說明

## API 文件
詳細 API 文件連結

## 貢獻
CONTRIBUTING.md 連結

## 授權
MIT License - 請參閱 LICENSE 檔案
```

### 程式碼文件

- **公開 API：** 必須使用 JSDoc/docstrings 記錄
- **複雜邏輯：** 新增解釋性註解
- **架構決策：** 記錄在 `docs/architecture/`
- **API 端點：** 維護 OpenAPI/Swagger 文件

### 行內文件

```javascript
// 良好：解釋「為什麼」
// 使用指數退避重試以處理網路不穩定
await retryWithBackoff(apiCall, { maxAttempts: 4 });

// 不佳：解釋「做什麼」（程式碼已經說明）
// 呼叫重試函式與 api call
await retryWithBackoff(apiCall, { maxAttempts: 4 });
```

---

## AI 助理工作流程

### 作為 Claude Code 助理時

#### 1. 理解任務
- 仔細閱讀使用者的請求
- 如果需求不明確，提出澄清問題
- 開始前檢查現有程式碼和慣例

#### 2. 規劃階段
- 對複雜的多步驟任務使用 `TodoWrite` 工具
- 將大型任務分解為較小、可管理的步驟
- 在實作前向使用者展示計劃（針對重大變更）

#### 3. 實作階段
- 編輯前先讀取現有檔案
- 優先編輯現有檔案而非建立新檔案
- 遵循現有的程式碼模式和慣例
- 撰寫安全的程式碼（避免 OWASP Top 10 漏洞）
- 包含錯誤處理和驗證

#### 4. 測試階段
- 執行現有測試以確保沒有退化
- 為新功能新增測試
- 驗證實作是否如預期運作

#### 5. 文件階段
- 更新相關文件
- 為複雜邏輯新增程式碼註解
- 針對重大變更更新 CHANGELOG.md

#### 6. 提交階段
- 撰寫清晰、描述性的提交訊息
- 遵循提交訊息格式慣例
- 適當時使用共同作者署名
- **僅在使用者明確要求時提交**

#### 7. 推送階段
- 使用 `git push -u origin <branch-name>`
- 驗證分支名稱以 `claude/` 開頭
- 網路錯誤時重試（最多 4 次，採用指數退避）

### 工具使用最佳實踐

1. **檔案操作：**
   - 使用 `Read` 而非 `cat`
   - 使用 `Edit` 而非 `sed/awk`
   - 使用 `Write` 而非 `echo >>`
   - 使用 `Glob` 而非 `find` 或 `ls`
   - 使用 `Grep` 而非 `grep` 或 `rg`

2. **程式碼探索：**
   - 對廣泛的程式碼庫探索使用 `Task` 工具，設定 `subagent_type=Explore`
   - 對特定檔案/模式搜尋使用直接工具（`Grep`、`Glob`）
   - 探索多個區域時並行讀取檔案

3. **並行執行：**
   - 並行執行獨立的工具呼叫
   - 僅在存在依賴關係時進行順序呼叫
   - 絕不在工具參數中使用佔位符

### 溝通風格

- 簡潔且技術性
- 除非明確要求，否則避免使用表情符號
- 專注於事實和問題解決
- 使用 `檔案:行號` 格式的程式碼參考
- 不需要不必要的讚美或驗證

---

## 進場策略與持倉監控

### 最佳進場點估算

#### 1. 技術面進場訊號

**價格位置評估：**
```python
進場條件組合：

A. 相對低點策略
├── 股價接近 20 日均線支撐
├── RSI < 30（超賣區）
├── 本益比低於產業平均 20%
└── 近 5 日出現放量（成交量 > 20日均量 1.5倍）

B. 突破策略
├── 股價突破 60 日均線
├── MACD 黃金交叉
├── 成交量放大確認突破
└── 搭配財報利多消息

C. 定期定額策略
├── 不看技術面
├── 每月固定日期（如每月 1 號）
├── 根據股票池權重分配
└── 適合長期投資者
```

**量化評分系統：**
```python
def calculate_entry_score(stock_data):
    """
    計算進場評分（0-100分）
    """
    score = 0

    # 本益比分數（30分）
    if pe_ratio < industry_median * 0.8:
        score += 30
    elif pe_ratio < industry_median:
        score += 20

    # 獲利品質（25分）
    if consecutive_profitable_quarters >= 4:
        score += 25
    elif consecutive_profitable_quarters >= 2:
        score += 15

    # 技術面（25分）
    if rsi < 30:
        score += 10
    if price_near_support:
        score += 10
    if volume_surge:
        score += 5

    # 板塊強度（20分）
    if sector_ranking <= 3:  # 前三強板塊
        score += 20
    elif sector_ranking <= 5:
        score += 10

    return score

# 建議：score >= 70 才考慮進場
```

#### 2. 基本面進場時機

**財報公布後的最佳時機：**
```
台股財報公布時程：
├── Q1 財報：5月15日前
├── Q2 財報（半年報）：8月31日前
├── Q3 財報：11月14日前
└── Q4 財報（年報）：3月31日前

建議進場時間點：
1. 財報公布後 3-5 個交易日
   └── 市場消化完利多/利空

2. 除權息前 1-2 個月
   └── 提前卡位領股息

3. 法說會後
   └── 確認公司展望
```

**進場檢查清單：**
```markdown
□ 最新一季 EPS 成長 > 10%
□ 毛利率維持或提升
□ 營收年增率 > 0
□ 自由現金流為正
□ 負債比 < 50%
□ 本益比 < 產業中位數
□ 無重大訴訟或負面新聞
□ 董監持股質押率 < 30%
□ 外資持股比例穩定或增加
□ 法人買超天數 > 5 天
```

#### 3. 資金配置策略

**分批進場法：**
```
總資金 100萬範例：

第一批（30%）：30萬
└── 條件：進場評分 >= 70

第二批（30%）：30萬
└── 條件：股價下跌 5-8% 或評分提升至 80

第三批（30%）：30萬
└── 條件：股價再跌 5-8% 或出現明確反轉訊號

保留現金（10%）：10萬
└── 緊急應變或加碼最佳標的
```

**單一股票配置上限：**
```
保守型：單一持股 ≤ 5%（20 檔分散）
穩健型：單一持股 ≤ 8%（12-15 檔）
積極型：單一持股 ≤ 10%（10 檔）

板塊集中度：
單一板塊 ≤ 30%（避免系統性風險）
```

### 進場後監控機制

#### 1. 每日監控項目

**自動化監控清單：**
```python
daily_monitoring = {
    "價格警報": {
        "停利點": "+15% 通知",
        "停損點": "-8% 警告, -10% 強制出場",
        "技術破位": "跌破 20日均線 警告"
    },

    "成交量異常": {
        "爆量": "成交量 > 20日均量 3倍",
        "量縮": "成交量 < 20日均量 0.3倍"
    },

    "籌碼變化": {
        "外資": "單日買賣超 > 1000張",
        "投信": "單日買賣超 > 500張",
        "自營商": "單日買賣超 > 500張"
    },

    "技術指標": {
        "RSI": "超買 > 70 或 超賣 < 30",
        "KD": "死亡交叉或黃金交叉"
    }
}
```

**Line 通知範例：**
```
📊 每日持倉報告 - 2025/11/20

✅ 正常股票（15檔）
⚠️ 需關注（3檔）
   - 2330 台積電：跌破20日均線
   - 2454 聯發科：外資連續賣超3天
   - 2881 富邦金：RSI進入超賣區

❌ 觸及停損（1檔）
   - 2303 聯電：跌幅-10%，建議出場

💰 整體績效：+5.2%
📈 今日漲跌：-0.8%
```

#### 2. 每週監控重點

**週報分析項目：**
```markdown
1. 持倉股票健診
   □ 檢視每檔股票的技術面變化
   □ 確認基本面是否惡化
   □ 檢查是否偏離買進邏輯

2. 股票池再平衡評估
   □ 是否有新的優質股票進入條件
   □ 現有持股是否該調整權重
   □ 板塊配置是否需要調整

3. 績效分析
   □ 與大盤比較（Alpha）
   □ 夏普比率計算
   □ 最大回撤檢視

4. 風險檢查
   □ 單一持股是否過度集中
   □ 相關性是否過高
   □ 是否有黑天鵝風險
```

#### 3. 每月回顧與調整

**月度再平衡流程：**
```python
def monthly_rebalance():
    """
    每月再平衡檢查清單
    """

    # 1. 篩選出場標的
    sell_list = []
    for stock in portfolio:
        if (stock.pe_ratio > industry_median * 1.5 or
            stock.consecutive_loss_quarters >= 2 or
            stock.rank_score < 60):
            sell_list.append(stock)

    # 2. 篩選進場標的
    new_candidates = screen_stocks({
        'pe_ratio': {'max': 15},
        'roe': {'min': 10},
        'eps_growth': {'min': 5}
    })

    # 3. 權重調整
    rebalance_weights(target_allocation)

    # 4. 產生交易清單
    return generate_trade_orders(sell_list, new_candidates)
```

**調整觸發條件：**
```
必須調整：
├── 個股虧損 > -15%（檢討是否停損）
├── 個股獲利 > +30%（考慮部分獲利了結）
├── 基本面重大惡化（如連續兩季虧損）
└── 爆發重大利空（如財報作假、掏空）

可以考慮調整：
├── 股價偏離合理價值 > 20%
├── 更優質標的出現
├── 板塊輪動訊號明確
└── 總體經濟環境改變
```

#### 4. 關鍵財務指標監控

**財報公布後必看指標：**
```markdown
獲利能力：
□ EPS（每股盈餘）：是否符合預期
□ 毛利率：是否維持穩定
□ 營業利益率：是否成長
□ ROE（股東權益報酬率）：> 10% 為佳

成長性：
□ 營收年增率
□ EPS 年增率
□ 每股淨值增長率

安全性：
□ 流動比率：> 150%
□ 速動比率：> 100%
□ 負債比率：< 50%
□ 利息保障倍數：> 5倍

現金流：
□ 營業現金流：持續為正
□ 自由現金流：充裕程度
□ 現金股利發放率：30-70% 為佳
```

#### 5. 風險事件應對

**不同風險等級的處理方式：**
```
🟢 低風險事件（觀察即可）
└── 單日跌幅 < 5%
└── 外資小幅賣超
└── 產業短期利空

🟡 中風險事件（加強監控）
└── 單日跌幅 5-8%
└── 跌破重要支撐
└── 法人連續賣超 3 天
└── 財報不如預期

🔴 高風險事件（考慮減碼或出場）
└── 單日跌幅 > 10%
└── 連續兩季虧損
└── 重大會計問題
└── 董事長或總經理異動
└── 爆發重大訴訟

⚫ 極端風險（立即出場）
└── 掏空或財報不實
└── 全額交割股或打入警示股
└── 下市風險
└── 重大違法事件
```

### 監控系統自動化

**建議的自動化架構：**
```python
# 監控系統架構
monitoring_system/
├── data_collector.py       # 每日收集股價、財報資料
├── alert_engine.py         # 警報引擎
├── performance_tracker.py  # 績效追蹤
├── risk_monitor.py         # 風險監控
├── notification.py         # Line/Email 通知
└── dashboard.py           # 視覺化儀表板

# 排程設定
Schedule:
├── 09:00 - 收盤價更新
├── 14:00 - 盤中監控（每小時）
├── 15:00 - 收盤後分析
├── 18:00 - 發送每日報告
└── 週日 20:00 - 週報產生
```

---

## 未來開發藍圖

### 階段 1：專案初始化（目前）
- [x] 建立儲存庫
- [x] 新增 LICENSE
- [x] 新增測試檔案用於工作流程驗證
- [x] 建立 CLAUDE.md 文件
- [ ] 建立 README.md
- [ ] 新增 .gitignore
- [ ] 確定專案目的和技術堆疊

### 階段 2：專案設定
- [ ] 初始化套件管理器
- [ ] 設定專案結構
- [ ] 設定建置工具
- [ ] 設定測試框架
- [ ] 設定 linting 和格式化
- [ ] 設定 pre-commit hooks

### 階段 3：核心開發
- [ ] 實作核心功能
- [ ] 撰寫測試
- [ ] 建立 API 文件
- [ ] 設定 CI/CD 管線

### 階段 4：文件與完善
- [ ] 完成使用者文件
- [ ] 新增程式碼範例
- [ ] 建立貢獻指南
- [ ] 準備首次發布

---

## 給儲存庫擁有者的問題

為了更好地協助開發，請澄清：

1. **專案目的：** topsteps_code 的目的是什麼？
2. **技術堆疊：** 應該使用哪些程式語言/框架？
3. **目標使用者：** 誰會使用這個專案？
4. **主要功能：** 要實作的主要功能是什麼？
5. **時間表：** 是否有任何截止日期或里程碑？
6. **整合：** 是否會與其他系統整合？
7. **部署：** 將部署在哪裡（雲端、本地等）？

---

## 參考資源

### 台股資料來源（免費）

#### 1. 台灣證券交易所（TWSE）開放資料
**官方網站：** https://www.twse.com.tw/

**主要 API 端點：**
```python
# 每日收盤行情
https://www.twse.com.tw/exchangeReport/MI_INDEX
參數：date=20251120&type=ALLBUT0999

# 個股日成交資訊
https://www.twse.com.tw/exchangeReport/STOCK_DAY
參數：stockNo=2330&date=20251120

# 三大法人買賣超
https://www.twse.com.tw/fund/T86
參數：date=20251120

# 融資融券餘額
https://www.twse.com.tw/exchangeReport/MI_MARGN
參數：date=20251120

# 每月營收
https://mops.twse.com.tw/nas/t21/sii/t21sc03_[年度]_[月份].html
```

**重要說明：**
- 完全免費，無需註冊
- 資料延遲約 15-20 分鐘（非即時）
- 僅提供上市公司資料（櫃買股票需至 TPEx）
- 資料格式通常為 JSON 或 CSV
- 建議加上 User-Agent 避免被擋

**使用範例：**
```python
import requests
import pandas as pd
from datetime import datetime

def get_twse_stock_day(stock_id, year_month):
    """
    取得個股每日成交資訊
    stock_id: 股票代碼（如 '2330'）
    year_month: 年月（如 '20251101'）
    """
    url = "https://www.twse.com.tw/exchangeReport/STOCK_DAY"
    params = {
        'response': 'json',
        'date': year_month,
        'stockNo': stock_id,
    }
    headers = {
        'User-Agent': 'Mozilla/5.0'
    }

    res = requests.get(url, params=params, headers=headers)
    data = res.json()

    if data['stat'] == 'OK':
        df = pd.DataFrame(data['data'], columns=data['fields'])
        return df
    return None

# 使用範例
df = get_twse_stock_day('2330', '20251101')
print(df.head())
```

#### 2. 櫃買中心（TPEx）開放資料
**官方網站：** https://www.tpex.org.tw/

**主要 API 端點：**
```python
# 上櫃股票每日收盤行情
https://www.tpex.org.tw/web/stock/aftertrading/daily_close_quotes/stk_quote_result.php
參數：l=zh-tw&d=113/11/20

# 上櫃股票三大法人買賣超
https://www.tpex.org.tw/web/stock/3insti/daily_trade/3itrade_hedge_result.php
參數：l=zh-tw&se=EW&t=D&d=113/11/20
```

**注意事項：**
- 櫃買中心的日期格式為民國年（113/11/20 = 2024/11/20）
- 需要轉換日期格式

#### 3. 公開資訊觀測站（MOPS）
**官方網站：** https://mops.twse.com.tw/

**可取得資料：**
- 財務報表（季報、年報）
- 每月營收
- 股利政策
- 董監持股
- 重大訊息公告

**營收資料範例：**
```python
# 上市公司每月營收
https://mops.twse.com.tw/nas/t21/sii/t21sc03_[年度]_[月份].html

# 範例：2024年11月營收
https://mops.twse.com.tw/nas/t21/sii/t21sc03_113_11.html
```

#### 4. FinMind 台灣股市資料
**官方網站：** https://finmindtrade.com/
**GitHub：** https://github.com/FinMind/FinMind

**特色：**
- Python 套件，易於使用
- 整合多種台股資料
- 提供免費額度（每日 500 次請求）
- 付費版約 3,000 元/年（無限請求）

**安裝與使用：**
```python
# 安裝
pip install FinMind

# 使用範例
from FinMind.data import DataLoader

api = DataLoader()

# 台股股價資料
df = api.taiwan_stock_daily(
    stock_id='2330',
    start_date='2024-01-01',
    end_date='2024-11-20'
)

# 台股財報資料
df_financial = api.taiwan_stock_financial_statement(
    stock_id='2330',
    start_date='2023-01-01'
)

# 本益比、股價淨值比
df_pe = api.taiwan_stock_per_pbr(
    stock_id='2330',
    start_date='2024-01-01'
)
```

#### 5. yfinance（Yahoo Finance）
**GitHub：** https://github.com/ranaroussi/yfinance

**台股代碼格式：**
```python
import yfinance as yf

# 台股代碼需加上 .TW（上市）或 .TWO（上櫃）
tsmc = yf.Ticker("2330.TW")  # 台積電（上市）
aic = yf.Ticker("3406.TWO")  # 玉晶光（上櫃）

# 取得歷史股價
hist = tsmc.history(period="1y")

# 取得財務資訊
info = tsmc.info
print(f"本益比: {info.get('trailingPE')}")
print(f"股價淨值比: {info.get('priceToBook')}")
```

**限制：**
- 財務資料較不完整
- 偶爾會有資料缺失
- 建議搭配其他資料源使用

#### 6. 資料比較表

| 資料來源 | 費用 | 完整度 | 即時性 | 易用性 | 建議用途 |
|---------|------|--------|--------|--------|----------|
| TWSE API | 免費 | ⭐⭐⭐⭐ | 延遲15分 | ⭐⭐⭐ | 股價、籌碼 |
| TPEx API | 免費 | ⭐⭐⭐⭐ | 延遲15分 | ⭐⭐⭐ | 櫃買股票 |
| MOPS | 免費 | ⭐⭐⭐⭐⭐ | 季度更新 | ⭐⭐ | 財報資料 |
| FinMind | 免費/付費 | ⭐⭐⭐⭐ | 日更新 | ⭐⭐⭐⭐⭐ | 全方位開發 |
| yfinance | 免費 | ⭐⭐⭐ | 延遲 | ⭐⭐⭐⭐ | 快速原型 |
| TEJ | 付費 | ⭐⭐⭐⭐⭐ | 日更新 | ⭐⭐⭐⭐⭐ | 專業研究 |

**建議組合：**
```
個人開發（免費）：
├── 股價資料：TWSE/TPEx API 或 FinMind 免費版
├── 財報資料：MOPS + FinMind
└── 快速測試：yfinance

小型團隊（預算 5 萬內）：
├── FinMind 付費版（3,000/年）
├── 基礎雲端服務
└── 必要時補充 TEJ 學術版

專業機構（預算充足）：
└── TEJ 完整版（35,000/年起）
```

### Git & GitHub
- [Git 文件](https://git-scm.com/doc)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Conventional Commits](https://www.conventionalcommits.org/)

### 安全性
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [安全最佳實踐](https://cheatsheetseries.owasp.org/)

### 量化交易資源
- [QuantConnect](https://www.quantconnect.com/) - 量化回測平台
- [Backtrader 文件](https://www.backtrader.com/docu/) - Python 回測框架
- [TA-Lib](https://ta-lib.org/) - 技術分析指標庫
- [台灣量化交易社群](https://www.facebook.com/groups/quantitative.trading.tw/)

### Claude Code
- [Claude Code 文件](https://docs.claude.com/en/docs/claude-code/)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)

---

## 變更日誌

### 2025-11-20
- 建立完整的 CLAUDE.md 文件
- 記錄目前儲存庫狀態
- 建立開發指南和慣例
- 定義 git 工作流程和分支策略
- 新增 AI 助理工作流程說明
- **新增「進場策略與持倉監控」章節**
  - 最佳進場點估算（技術面、基本面、資金配置）
  - 每日/每週/每月監控機制
  - 關鍵財務指標監控
  - 風險事件應對策略
  - 自動化監控系統架構
- **新增台股免費資料來源資訊**
  - TWSE（台灣證券交易所）公開 API
  - TPEx（櫃買中心）開放資料
  - MOPS（公開資訊觀測站）
  - FinMind、yfinance 使用說明
  - 資料來源比較表與建議組合

### 2025-10-08
- 使用 MIT License 初始化儲存庫
- 新增 test.txt 用於工作流程驗證
- 首次與 Claude 協作的提交

---

## 聯絡與支援

- **儲存庫擁有者：** CIOU,GUO-YU (jack chiou)
- **GitHub Issues：** https://github.com/zxcvbn1294/topsteps_code/issues
- **Claude Code 回饋：** https://github.com/anthropics/claude-code/issues

---

**注意：** 此文件應隨專案演進而更新。當專案結構、慣例或工作流程有重大變更時，請相應更新此檔案。
