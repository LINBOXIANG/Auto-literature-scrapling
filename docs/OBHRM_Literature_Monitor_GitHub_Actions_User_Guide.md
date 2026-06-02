# OBHRM Literature Monitor 微信群快速版

用途：输入关键词、时间窗口、期刊列表，自动生成 OBHRM/HCI/preprint 文献周报网页。

```text
打开项目仓库
  ↓
Fork 到自己的 GitHub 账号
  ↓
进入自己 fork 后的仓库
  ↓
Settings → Pages → 选择 GitHub Actions
  ↓
Actions → Generate OBHRM Literature Report
  ↓
Run workflow
  ↓
填写检索条件
  ↓
等待绿色进度条完成
  ↓
打开 Public report 链接查看 HTML 周报
```

## 仓库地址

```text
https://github.com/qlq20011120/Auto-literature-scrapling
```

## 表单填写路径

```text
Keywords
  ↓
每行一个关键词，最多 5 个；空白框会被忽略

Match mode
  ↓
any = 命中任意关键词即可
all = 必须同时命中所有关键词

Timezone
  ↓
Asia/Tokyo = 日本时间
America/Chicago = 美国中部时间
Asia/Shanghai = 北京时间

Time window
  ↓
start_date  + start_clock = 开始时间
end_date    + end_clock   = 结束时间
例：2026/05/18 + 00:00 到 2026/05/25 + 00:00

Journal lists
  ↓
可多选，系统自动取并集
默认 abs-4-star，最精简

Run workflow
  ↓
开始生成报告
```

## 推荐模板

```text
keyword_1: Presenteeism
keyword_2:
keyword_3:
keyword_4:
keyword_5:

match_mode: any
timezone: Asia/Tokyo

start_date: 2026/05/18
start_clock: 00:00
end_date: 2026/05/25
end_clock: 00:00

journal lists: 勾选 abs-4-star
public_site_url: 留空
push_lark: 按需要选择
```

## 多关键词并逻辑示例

```text
keyword_1: Organizational Behavior
keyword_2: Asia
keyword_3: Asian
keyword_4: Engagement
keyword_5:

match_mode: all
journal lists: abs-4-star + ft50
```

含义：只保留同时命中这四个关键词的文章，并在 `abs-4-star` 与 `ft50` 的并集中检索。

## 结果在哪里看

```text
workflow 完成
  ↓
打开本次 workflow run
  ↓
查看 Summary
  ↓
点击 Public report
  ↓
查看 HTML 文献周报
```

也可以在 workflow 页面底部下载 `Artifacts`，里面有：

```text
HTML report
Markdown report
CSV records
scan trace
run log
```

## 注意事项

```text
看不到 Run workflow
  → 先 Fork 到自己的账号，再在自己的仓库里运行

网页报告 404
  → 等 1-2 分钟，或检查 Settings → Pages 是否为 GitHub Actions

结果太多
  → 用 abs-4-star，缩短时间窗口，或把 match_mode 改成 all

只想输入一个关键词
  → 只填 keyword_1，其他关键词框留空

全文下载
  → 本工具不自动登录、不下载 PDF；请用自己的学校权限手动访问 DOI
```

