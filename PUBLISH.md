# 发布到你自己的 GitHub

整套可复制的终端命令。先把这个文件夹（`开源_wechat-mp-layout/`）整个拷到你电脑上任意位置，再操作。

## 准备

- 装好 git（终端输 `git --version` 能出版本号就行）
- 有一个 GitHub 账号
- 建议也装 GitHub CLI（`gh`）：`brew install gh`，然后 `gh auth login` 登录一次

> ⚠️ 这个文件夹里有一个**半成品 `.git`**（自动化环境里残留的，没法在那边删）。所以下面命令第一步都先 `rm -rf .git` 清干净再 `git init`，照抄即可。
>
> 文件夹位置：`~/Downloads/工作中/内容创作/开源_wechat-mp-layout`

## 方式一 · 用 GitHub CLI（最快）

```bash
cd ~/Downloads/工作中/内容创作/开源_wechat-mp-layout   # 进到这个文件夹
rm -rf .git                         # 清掉残留的半成品 .git
git init
git add .
git commit -m "init: 公众号排版 四风格（提示词 + 技能）"
gh repo create wechat-mp-layout --public --source=. --remote=origin --push
```

跑完会直接给你一个 GitHub 仓库链接，开源完成。

## 方式二 · 不用 CLI（手动建仓库）

1. 浏览器打开 https://github.com/new ，仓库名填 `wechat-mp-layout`，选 Public，**不要**勾初始化 README，点 Create。
2. 回终端：

```bash
cd ~/Downloads/工作中/内容创作/开源_wechat-mp-layout
rm -rf .git                         # 清掉残留的半成品 .git
git init
git add .
git commit -m "init: 公众号排版 四风格（提示词 + 技能）"
git branch -M main
git remote add origin https://github.com/你的用户名/wechat-mp-layout.git
git push -u origin main
```

把 `你的用户名` 换成你的 GitHub 用户名即可。

## 发布后建议

- 在仓库 Settings → 给个 Description 和 Topics（如 `wechat`、`prompt`、`ai`、`typesetting`）
- 把 README 里 `assets/demo.png` 换成真实截图，首页更直观
- 之后改了 `PROMPT.md` / `SKILL.md`，记得 `git add . && git commit -m "..." && git push` 同步

## 不要提交的东西

这个开源包是**纯排版**的，本身不含任何隐私。但如果你往里加东西，注意别提交：
- 任何 API Key、`.env`
- 你的人群画像、选题/写作的私有 SOP、人设语料（这些是你的核心资产，留私有仓库）
