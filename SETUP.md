# GitHub 主页美化（Profile README）使用说明

## 1) 创建正确的仓库

- GitHub 新建一个仓库：仓库名必须等于你的用户名，例如 `seele/seele`
- 你的用户名是 `1lck`，所以应该是 `1lck/1lck`
- 公开仓库（Public）
- 勾选 “Add a README file”（或者把本仓库内容推上去）

## 2) 替换占位符

打开 `README.md`，替换这些字段：

- 本仓库已为 `1lck` 预填；你可以按需修改：姓名、简介、置顶项目、技能图标、配色
- 如果你想展示邮箱，把 README 里的 Email badge 加回去并填上地址

## 3) 可选：启用 Snake 动画（推荐）

文件：`.github/workflows/snake.yml`

1. 进入 GitHub 仓库 → Settings → Actions → General
2. `Workflow permissions` 选择 “Read and write permissions”
3. 手动运行一次 Action 或等待定时任务

说明：生成的 SVG 会提交到 `output` 分支（包含 `snake.svg` 和 `trophy.svg`），README 里通过 raw 链接引用。

## 4) 可选：启用 Metrics 大卡片（更炫）

文件：`.github/workflows/metrics.yml`

默认会优先使用 `METRICS_TOKEN`，没有的话会退回用仓库自带的 `GITHUB_TOKEN`（部分数据/插件可能受限）。

提示：`Achievements` 插件偶尔会因为 GitHub 限流/反爬或权限不足显示 `Unexpected error`，建议配置 `METRICS_TOKEN` 后再手动运行一次 `metrics`。

1. （可选）GitHub → Settings → Developer settings → Personal access tokens
2. （可选）创建 Fine-grained token（最小权限，只授权当前仓库即可）
3. （可选）仓库 Settings → Secrets and variables → Actions → New repository secret
4. （可选）新建 secret：`METRICS_TOKEN` = 你的 token
5. 手动运行一次 Action（或等待定时任务）

说明：该工作流会生成两个文件：

- `github-metrics.svg`（综合卡片）
- `contributions.svg`（贡献绿墙/日历，默认显示近 3 年）

如果你不想用 token，可以注释掉 README 里的 Metrics 部分（以及 Contributions 的图片引用）。

## 5) 可选：启用 Streak 连续打卡

`Streak` 属于第三方服务，有时会因为 GitHub API 限流而显示失败。想要稳定展示，建议自部署（Vercel/Heroku 等）：

- 项目说明：https://github.com/DenverCoder1/github-readme-streak-stats

部署完成后，把 README 里的 Streak 图片地址换成你自己的部署地址即可。
