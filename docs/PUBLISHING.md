# 🎵每周歌曲推荐榜｜Durable Publish Layer

本仓库用于长期保存《🎵每周歌曲推荐榜》的正式 HTML 周榜，避免 ChatGPT 计划任务临时附件出现“此文件已过期 / 找不到此文件”。

## 固定目标

- Repository：`lynelletu-ux/my-weekly-music-picks`
- Branch：`main`
- GitHub Pages Source：`main /docs`
- 历史归档：`docs/index.html`
- 正式周榜：`docs/issues/YYYY/issue-NN.html`
- Pages 根地址：`https://lynelletu-ux.github.io/my-weekly-music-picks/`
- 单期地址：`https://lynelletu-ux.github.io/my-weekly-music-picks/issues/YYYY/issue-NN.html`
- Commit：`publish: weekly music issue NN`

底层 URL 路径只使用小写英文字母、数字、连字符和斜杠。中文标题与 emoji 只用于页面内标题和聊天入口文字。

## 正式发布顺序

1. 完成候选筛选、历史去重和 Apple Music CN 精准核验。
2. 生成最终单文件 HTML，沿用已确认的无图深色 Editorial Music Journal 版式。
3. 执行 HTML QC：UTF-8、移动端可读、无 `<img>`、每首歌 Apple Music 按钮为具体 song URL。
4. 根据已成功发布的正式历史确定期号，不得因失败重试而跳号或重置。
5. 写入 `docs/issues/YYYY/issue-NN.html`。
6. 重新读取 GitHub 文件，核对日期、期号、标题和内容。
7. 检查对应 GitHub Pages HTTPS URL。若短暂 404，标记为部署 pending 并复核同一 URL，不得新建重复期号。
8. Pages 页面可访问后，更新 `docs/index.html`，将新一期置顶。
9. 最终聊天层只推送一个稳定 Pages 入口，不再把 sandbox 临时附件作为正式交付。

## 聊天展示

链接文字必须严格为：

`🎵每周歌曲推荐榜｜YYYY.MM.DD｜第NN期.html`

链接目标必须为该期 GitHub Pages URL，不得使用 `sandbox:/mnt/data/...`。

## 内容规则

- HTML 内容、版式、推荐逻辑、Apple Music 精准直达按钮保持现行规则。
- 正式取消所有歌曲封面、专辑封面、歌手头像及其它图片。
- Apple Music 精准链接只存在于 HTML 内。
- 聊天层不显示 Apple Music 卡片、播放器、搜索结果卡、单曲 URL 或歌单正文。

## 失败恢复

- GitHub 写入失败：不消耗新期号，不发送伪造链接。
- 文件已写入但 Pages 尚未部署：保持 pending，并复核同一路径。
- 不因失败重试而创建第二个同期期号或重复文件。
