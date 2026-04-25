# 刷题Box

<p align="center">
  <img src="https://img.shields.io/badge/平台-Web%20%7C%20Android-blue" alt="Platform">
  <img src="https://img.shields.io/badge/单文件-HTML-green" alt="Single File">
  <img src="https://img.shields.io/badge/语言-中文-orange" alt="Language">
  <img src="https://img.shields.io/badge/license-MIT-lightgrey" alt="License">
</p>

一款轻量、美观、功能丰富的刷题应用。支持多种题型、错题本、考试模式、AI 解析、积分排行榜等功能，所有逻辑集成在单个 HTML 文件中，无需构建、无需后端即可运行。

## 在线体验

- GitHub Pages：[https://zaixiaxingzhang.github.io/Quiz-Box/](https://zaixiaxingzhang.github.io/Quiz-Box/)
- Netlify 镜像：[https://shuatiweb.netlify.app/](https://shuatiweb.netlify.app/)

> 两个地址内容完全一致，选择访问速度更快的即可。

## APK 版本

本项目提供 Android APK 安装包，可在手机上原生运行，获得更流畅的体验和更好的离线支持。

## 功能一览

### 题库管理

| 功能 | 说明 |
|------|------|
| 文件夹管理 | 创建、编辑、删除题库文件夹，按科目 / 分类自由组织 |
| 多题型支持 | 单选题、判断题、填空题，满足不同刷题需求 |
| 图片题目 | 支持题目包含图片，通过 ZIP 压缩包导入带图题 |
| JSON 导入/导出 | 标准 JSON 格式导入导出题库，方便备份与分享 |
| ZIP 导入 | 将 JSON + 图片打包为 ZIP 一次性导入 |
| 链接导入 | 输入直链 URL 远程导入题库，支持网盘下载链接 |
| 题库体检 | 自动检测题库格式问题（缺答案、选项重复、编码异常等），一键排查 |
| AI 转换题库 | 借助 AI 大模型将 Word 文本、截图 OCR 等任意格式自动转为可导入的 JSON |
| 批量操作 | 批量选择题目进行移动、删除等操作 |
| 搜索 | 全局搜索题目内容，快速定位 |

### 刷题练习

| 功能 | 说明 |
|------|------|
| 练习模式 | 按文件夹逐题练习，即时显示对错与解析 |
| 考试模式 | 计时模拟考试，可自定义题数、时长、是否打乱选项 |
| 错题本 | 自动收录做错的题目，连续答对 2 次自动移出错题本 |
| 收藏夹 | 星标题目，针对性复习 |
| 题目解析 | 每道题支持查看详细解析 |
| 兼容模式 | 可关闭选项乱序，适合选项与位置绑定的题目 |
| 答题进度 | 顶部进度条实时显示做题进度 |

### AI 助手

| 功能 | 说明 |
|------|------|
| 问 AI | 在做题页面一键唤起 AI 对话，智能解析题目 |
| 流式输出 | AI 回复实时流式显示，含思考过程折叠展示 |
| 保存解析 | 可将 AI 回复一键保存为题目解析，支持追加或覆盖 |
| 多模型支持 | 兼容 OpenAI API 格式的各类大模型，可自定义 API 地址和密钥 |
| Markdown 渲染 | AI 回复支持代码块、表格、数学公式等富文本渲染 |

### 成长与激励

| 功能 | 说明 |
|------|------|
| 经验等级 | 做题获取经验值，1-100 级成长体系 |
| 等级徽标 | 达到 50/80/100 级分别获得铜标、银标、金标 |
| 积分系统 | 做对题目、完成任务获得积分 |
| 每日任务 | 4 个每日任务（日常签到、初见成效、温故知新、完美通关），自动领取奖励 |
| 学习日历 | 热力图展示每日学习时长，记录学习轨迹 |
| 学习计时 | 做题/考试期间自动累计学习时长 |

### 排行榜

| 功能 | 说明 |
|------|------|
| 全球排行 | 基于积分的全球排行榜，Supabase 后端驱动 |
| 登录注册 | 支持注册与登录，数据云端同步 |
| 管理后台 | 内置管理面板，支持封禁用户、清空积分等操作 |

### 外观与体验

| 功能 | 说明 |
|------|------|
| 深色模式 | 支持亮色 / 深色主题切换，过渡动画流畅 |
| 移动端适配 | 完全适配手机屏幕，支持安全区域（Safe Area） |
| 页面转场 | 类原生 App 的页面滑入滑出动画 |
| 手势支持 | 全屏图片查看支持双指缩放、单指平移 |
| 全屏图片 | 点击题目图片可全屏查看，支持缩放拖拽 |
| 离线运行 | 数据存储在本地 IndexedDB，无需联网即可使用核心功能 |

## 技术架构

- **单文件架构**：所有 HTML、CSS、JavaScript 集成在一个 `quiz-box.html` 文件中，无需构建工具
- **数据存储**：IndexedDB 为主，localStorage 为降级方案，完全本地化存储
- **页面路由**：自实现页面栈管理，支持多级页面推入与弹出
- **排行榜后端**：Supabase（PostgreSQL + Edge Functions）
- **AI 功能**：兼容 OpenAI Chat Completions API 格式，支持流式输出

## 题库 JSON 格式

题库采用 JSON 格式，UTF-8 编码，结构如下：

```json
[
  {
    "type": "single",
    "question": "中国的首都是哪里？",
    "options": ["上海", "北京", "广州", "深圳"],
    "answer": 1,
    "explanation": "北京是中华人民共和国的首都。"
  },
  {
    "type": "judge",
    "question": "地球是太阳系中最大的行星。",
    "answer": false,
    "explanation": "木星才是太阳系中最大的行星。"
  },
  {
    "type": "fill",
    "question": "水的化学式是____。",
    "answer": "H2O",
    "explanation": "水由两个氢原子和一个氧原子组成。"
  }
]
```

### 字段说明

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `type` | string | 是 | 题型：`single`（单选）、`judge`（判断）、`fill`（填空） |
| `question` | string | 是 | 题目内容 |
| `options` | string[] | 单选题必填 | 选项列表（仅单选题需要） |
| `answer` | number / boolean / string | 是 | 单选题为正确选项索引（从 0 开始），判断题为 `true`/`false`，填空题为答案字符串 |
| `explanation` | string | 否 | 题目解析 |

### 带图题目

带图片的题目需要使用 ZIP 压缩包导入，ZIP 内结构：

```
quiz-data.zip
├── data.json          # 题目数据，图片路径引用相对路径
└── images/
    ├── q1.png
    └── q2.jpg
```

在 JSON 中通过 `image` 字段引用图片：

```json
{
  "type": "single",
  "question": "下图所示的建筑是？",
  "image": "images/q1.png",
  "options": ["埃菲尔铁塔", "自由女神像", "大本钟", "比萨斜塔"],
  "answer": 0
}
```

## 快速开始

### 在线使用

直接访问在线地址即可使用，无需安装：

- [GitHub Pages](https://zaixiaxingzhang.github.io/Quiz-Box/)
- [Netlify](https://shuatiweb.netlify.app/)

### 本地运行

1. 下载 `quiz-box.html` 文件
2. 用浏览器直接打开即可运行
3. 或使用本地服务器：

```bash
# 使用 Python
python3 -m http.server 8080

# 使用 Node.js
npx serve .
```

### 部署到自己的服务器

只需将 `quiz-box.html` 放到任意静态文件服务器或 CDN 上即可，无需额外配置。

## 导入题库

### 方式一：文件导入

1. 点击首页右上角 **导入** 按钮
2. 选择 **文件导入**
3. 选择 `.json` 文件或 `.zip` 压缩包
4. 选择目标文件夹，确认导入

### 方式二：链接导入

1. 点击首页右上角 **导入** 按钮
2. 选择 **链接导入**
3. 粘贴 JSON 或 ZIP 文件的直链地址
4. 确认导入

> 提示：网盘下载链接也可以使用，复制浏览器地址栏中正在下载的链接（含 token 参数的长链接）即可。

### 方式三：AI 转换

1. 将任意格式的题目（Word 复制、截图 OCR、手打文字）发给 AI
2. 配合应用内置的 AI 提示词模板
3. AI 输出 JSON 后保存为 `.json` 文件
4. 可先用 **设置 → 工具 → 题库体检** 检测格式
5. 导入刷题Box 即可

## 常见问题

**Q：数据存储在哪里？会丢失吗？**

A：所有数据存储在浏览器的 IndexedDB 中，不会丢失。但清除浏览器数据会删除题库，建议定期通过导出功能备份。

**Q：支持哪些浏览器？**

A：推荐 Chrome、Edge、Safari 等现代浏览器。应用已针对旧版 WebView 做了兼容性处理。

**Q：排行榜数据存在哪里？**

A：排行榜数据存储在 Supabase 云端，需要注册登录才能参与排名。题库和做题记录始终保存在本地。

**Q：AI 功能需要配置什么？**

A：进入 **设置 → AI 功能配置**，开启 AI 功能并填写兼容 OpenAI 格式的 API 地址和密钥即可。支持 OpenAI、DeepSeek、通义千问等主流大模型。

**Q：APK 版本和网页版有什么区别？**

A：功能完全一致，APK 版本通过 WebView 封装，提供更好的全屏体验和桌面快捷方式支持。

## 项目结构

```
Quiz-Box/
├── quiz-box.html    # 应用主文件（包含全部 HTML/CSS/JS）
└── README.md        # 项目说明
```

## 致谢

- 字体：[Noto Sans SC](https://fonts.google.com/noto/specimen/Noto+Sans+SC)（Google Fonts）
- 排行榜后端：[Supabase](https://supabase.com/)
- 图标：内联 SVG，无需网络加载

## License

MIT License
