# design.md
# 美团小黄车档案 / Meituan Bike Archive

---

## 项目性质 / Project Nature

这是一个持续生长的城市观察档案。记录美团小黄车从第一代至今的结构性演化。

不设终点。不追求完整。只追求诚实。

选择只记录美团，本身就是一个立场。
定义什么是大版本，本身就是一个视角。
用客观的语言，呈现一个有立场的观察。

---

## 版本逻辑 / Version Logic

### 单车大版本（Bike Major Version）
格式：`V1.0` `V2.0` `V3.0`

结构性改变触发大版本号。判断标准：
- 锁具类型变化（实体锁 → 电子锁）
- 车轮条幅材质变化（黄色塑料 → 金属）
- 前叉结构变化（无减震 → 有减震）
- 车架形态的根本性重塑

### 小版本（Minor Version）
格式：`V1.1` `V1.2`

零件或表面升级，不触发大版本号：
- 涂装配色调整
- 座椅样式更换
- 把手配件增减（如挡风罩）
- 车篮形态微调

### 零件版本（Component Version）
格式：`WH1.0` `ST2.0` 等，见零件编号系统

### 旁支（Branch）
曾出现但未被继续迭代的方向，单独标注，不纳入主干版本线。视觉上降权处理（图片透明度 60%）。

---

## 已知版本现状 / Known Versions

| 版本 | 状态 | 特征 | 素材 |
|------|------|------|------|
| V1.0 | 已确认 | 实体锁，黄色塑料条幅 | 暂用网图占位，待补实拍 |
| V1.1 | 已确认 | 实体锁，金属条幅 | 已实拍 |
| V2.0 | 已确认 | 电子锁，前叉无减震 | 已实拍 |
| V2.1 | 已确认 | 电子锁，前叉无减震，细节迭代 | 暂用网图占位，待补实拍 |
| V3.0 | 已确认（最新） | 电子锁，前叉有减震 | 已实拍 |
| Mix版本 | 旁支 | 车头重新开模，金属条幅，未继续迭代 | 已实拍 |
| V0（ofo前身） | 排除 | DNA 断层太大，不纳入主干 | — |

> 注：V1.0 和部分版本实车已稀少，正在寻找实拍机会（含上海共享单车墓地）。占位图仅用于开发阶段，上线前全部替换为实拍。

---

## 零件编号系统 / Component Code System

| 零件 | 编号 | 示例版本号 |
|------|------|------------|
| Wheel 车轮 | WH | WH1.0 |
| Painting 涂装 | PT | PT1.0 |
| Seat 座椅 | ST | ST1.0 |
| Fender & Kickstand 挡泥板支架 | FK | FK1.0 |
| Basket 车篮 | BK | BK1.0 |
| Handle 把手 | HD | HD1.0 |
| Lock 车锁 | LK | LK1.0 |
| Pedal 脚踏 | PD | PD1.0 |
| QR Code 二维码 | QR | QR1.0 |
| Accessories 配件 | AC | AC1.0 |

---

## 信息架构 / Information Architecture

### 页面结构

```
首页 Home  /
└── 导航栏 nav
└── Gallery：所有大版本并列，时间线从左到右
    └── bike-card × N
        ├── bike-card-image（主视图，正侧面）
        ├── bike-version-label（如 V1.0，黑底白字）
        ├── bike-card-name（版本名，待定命名系统）
        └── bike-card-description（1-2句中文，克制）
└── 旁支区 gallery-branches
    ├── branch-divider
    ├── branch-label（标注 BRANCH）
    └── branch-card × N（样式同 bike-card，透明度 60%）
└── 页脚 footer

零件页 Components  /components
└── 导航栏 nav
└── 零件图标网格（手绘风格图标 + 编号 + Variants 数量）
    └── component-card × N
        ├── components-drawing（手绘图标）
        └── components-name（零件名 + X Variants）
└── 零件变体图片区
    └── component-variant-card × N
        ├── component-card-image（零件特写）
        ├── component-version-label（如 WH1.0，白底黑框）
        └── component-card-description（1-2句描述）

关于页 About  /about
└── 导航栏 nav
└── 文字介绍（中英双语）
└── 手绘插画
```

### 导航结构
左侧固定导航，三个入口：
- Bikes（首页）
- Components（零件页）
- What & why（关于页）

---

## 视觉方向 / Visual Direction

**核心原则：界面退后，内容说话。**

单车本身是黄色的。那个黄是这个项目唯一需要的颜色。UI 不添加情绪，不抢镜。

### 色彩系统 / Color Tokens

| 变量名 | 色值 | 用途 |
|--------|------|------|
| Background | #FAFAFA | 页面背景 |
| Text | #111111 | 主文字 |
| Text-Secondary | #999999 | 次要文字、标注 |
| Card-Background | #DADADA | 图片占位背景 |
| Label-Background | #000000 | 版本号标签背景（bike-version-label） |
| Drawing-Secondary | #EEEEEE | 手绘图标次要色 |

### 版本号标签视觉层级

- `bike-version-label`（V1.0）：黑底白字，实心，视觉权重高
- `component-version-label`（WH1.0）：白底黑框，轻一级，从属关系

### 字体 / Typography

| Style 名 | 字体 | 大小 | 用途 |
|----------|------|------|------|
| label | Technical | 11px | 导航、标签、全大写结构文字 |
| version | Technical | 24px | 版本号专用 |
| body | Technical（占位） | 14px | 正文描述（待换中文字体） |
| title | Technical | 32px | 页面标题 |

> 注：Technical 对中文支持差，正文中文字体待与 C 讨论后确定，建立独立 Text Style 替换。

### 排版 / Layout
- 桌面端优先，1440px 宽
- 大量留白，图片主导
- 页边距 64px，列间距 32px
- 不使用卡片阴影、渐变等常见 UI 套路

### 图片处理 / Photo Treatment
- 拍摄标准：正侧面，固定距离，固定构图比例
- 背景保留城市环境（不抠图），用统一裁切比例收拢差异
- 网图仅作临时占位，上线前全部替换为实拍

### 整体气质
档案美学。实验室标签感。严谨，旧旧的，但不沉重。
参考：Le Labo 产品标签语言，Bernd & Hilla Becher 档案摄影逻辑。

---

## 语言 / Language

- 正文描述：中文
- 版本号、标签、导航、结构性元素：英文
- About 页：中英双语

---

## 图层命名规范 / Layer Naming

```
页面
home
components
about

区块
nav
gallery
gallery-branches
footer

组件
bike-card
bike-card-image
bike-version-label
bike-card-name
bike-card-description

component-card
components-drawing
components-name
component-variant-card
component-card-image
component-version-label
component-card-description

nav-logo
nav-link-bikes
nav-link-components
nav-link-about

branch-divider
branch-label
branch-card
```

---

## 技术方向 / Technical Direction

- 形态：网站，桌面端优先
- 数据方案：方向二（代码与内容分离，数据存 JSON 文件）
- 后期可升级为方向三（带管理后台的动态网站），升级成本低

---

## 当前状态 / Current Status

- [x] 版本逻辑确定（3个大版本 + 旁支）
- [x] 零件编号系统确定
- [x] 视觉方向确定（档案美学，黑白中性底）
- [x] 色彩系统建立（6个变量）
- [x] Spacing 系统建立（8px 基数）
- [x] Typography 建立（4个 Text Style，占位）
- [x] 三个页面原型完成（Home / Components / About）
- [x] 图层命名规范确定
- [x] Cursor 安装完成
- [ ] 中文字体选型（待与 C 讨论）
- [ ] 版本命名系统（待与 C 讨论）
- [ ] 实拍素材补全（V1.0 / V2.1 暂用网图）
- [ ] Figma MCP 接入 Cursor
- [ ] 技术栈选型
- [ ] 开始开发
