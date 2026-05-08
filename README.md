# 竞品调研看板（独立预览）

跟 echo-app 主项目代码完全独立，**不影响**任何主项目逻辑。维护时只需要改这一个文件夹。

## 目录结构

```
preview/competitor-tracker/
├── index.html      ← 可视化页面（打开即看）
├── data.json       ← 数据源（要更新就改这个）
└── README.md       ← 本说明
```

## 怎么打开预览

终端里跑一行就行（任选其一）：

```bash
# 进到这个文件夹
cd preview/competitor-tracker

# 方式 1：Python（macOS 自带）
python3 -m http.server 8765

# 方式 2：Node
npx serve .
```

然后浏览器打开 <http://localhost:8765>。

> 不能直接双击 `index.html`，因为浏览器安全策略不允许 `file://` 协议读取本地 JSON。

## 怎么更新数据

1. 编辑 `data.json`
2. 浏览器刷新页面 → 立即看到最新效果

新增竞品参考已有条目格式追加到 `competitors` 数组。字段说明：

| 字段 | 类型 | 说明 |
|---|---|---|
| `id` | string | 唯一标识 |
| `name` | string | 显示名 |
| `category` | string | `publishing` / `auto-reply` / `review-mgmt` |
| `priceMin` / `priceMax` | number | 价格区间 |
| `priceUnit` | string | 单位文案 |
| `inBudget` | boolean | 是否在 $10–20 预算内 |
| `recommended` | boolean | 是否标记"推荐"徽章 |
| `rating` | number | 1–5 星 |
| `hasApi` | boolean | 是否有公开 API |
| `apiType` | string | API 类型描述 |
| `platforms` | string[] | 支持的平台 |
| `website` / `docs` | string | 链接 |
| `pros` / `cons` | string[] | 优势 / 风险列表 |
| `notes` | string | 备注 |

## 跟 docs/ 里的 Markdown 是什么关系

- `docs/competitor-integration-research.md` —— 完整调研文档，给团队内部看
- `docs/competitor-decision-brief.md` —— 一页纸决策版，给老板做选择
- `preview/competitor-tracker/` —— 可视化看板，给老板/合伙人远程看效果

三份内容同步；本看板的数据来自前两份的整理。
