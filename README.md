# Evolv.Share — 美团单车档案

一个记录美团小黄车（前身：摩拜单车）从第一代至今**结构性演化**的城市观察档案。

收录每一代车的整车形态、车架、车锁、车轮、涂装、车座、把手、挡泥板、车筐、脚踏、二维码等组件版本，并提供互动式浏览（拖拽 carousel、modal 放大、捏合缩放、UGC 上传）。

> An interactive city-observation archive that records the **structural evolution** of Meituan shared bikes (formerly Mobike) — from V1.0 to today. Each generation is broken down into component-level variants (frame, lock, wheel, paint, seat, handle, fender, basket, pedal, QR code…) so the lineage stays legible at a glance.

---

## 项目性质 / Project Nature

- **个人独立项目**，与美团 / Meituan 无任何商业或合作关系
- **观察式档案**：版本划分与判定标准基于作者的视角，不代表官方版本史
- **持续生长**：图片来源混合「自摄 + 网友投稿 + 网图」，会持续替换为统一观感的自摄图

---

## 版本列表 / Version List

### 整车 Bikes

| 版本 | 备注 |
|---|---|
| V0.2 | 摩拜末代（隐藏卡片，需在 carousel 上向左拉 ≥ 100px 解锁） |
| V1.0 | 美团收购摩拜后第 1 代，黄色塑料条幅 + 物理车锁 |
| V1.1 | 物理锁升级为蓝牙电子锁 |
| V2.1 | 第 2 代首次迭代，加入灰色搭配 + 色块分割设计 |
| V2.2 | 待补充 |
| V2.3 | 待补充 |
| V3.1 | 第 3 代首辆：取消色块、引入手机夹架 + 前叉减震 + 防护齿轮罩 |

### 组件 Components

| 组件 | 缩写 | 当前版本数 |
|---|---|---|
| 车轮 Wheel | WH | 4 |
| 涂装 Painting | PT | 7 |
| 车座 Seat | ST | 7 |
| 挡泥板和支架 Fender & Kickstand | FK | 6 |
| 车筐 Basket | BK | 4 |
| 把手/铃铛 Handle | HD | 5 |
| 车锁 Lock | LK | 5 |
| 脚踏 Pedal | PD | 5 |
| 二维码 QR Code | QR | 5 |
| 其他配件 Accessories | AC | 4 |

---

## 技术栈 / Tech Stack

- **前端**：纯静态 HTML / CSS / 原生 JavaScript（无框架）
- **字体**：Google Fonts — `Share Tech Mono` + 系统中文 fallback（PingFang SC / Hiragino Sans GB / Microsoft YaHei）
- **布局**：CSS clamp + flex + scroll-snap
- **交互**：原生 scroll/touch 事件，自实现 modal、捏合缩放、pull-to-reveal 阈值锁定、idle 期变体图预加载
- **UGC 收集**：飞书表单
- **托管 / Hosting**：GitHub Pages

> Plain static stack — HTML / CSS / vanilla JS. No build step, no framework. Hosted on GitHub Pages.

---

## 访问地址 / URL

- 站点 / Live site: <https://tangerinecamel.github.io/bike-archive/>
- 仓库 / Repo: <https://github.com/TangerineCamel/bike-archive>

---

## 本地运行 / Local Dev

```bash
# 克隆
git clone https://github.com/TangerineCamel/bike-archive.git
cd bike-archive

# 任意静态服务器即可，例如：
python3 -m http.server 8000
# 然后访问 http://localhost:8000
```

---

## 致谢 / Credits

照片暂时混合了网友投稿与网络公开图片，正在逐步替换为作者自摄。如有版权问题或愿意提供原图，请通过站内「我也想提供照片」入口联系。

> Photos currently mix community-submitted shots and openly available images; they're being gradually replaced with the author's own. If you spot a copyright concern or want to contribute, use the "我也想提供照片" link on the site.
