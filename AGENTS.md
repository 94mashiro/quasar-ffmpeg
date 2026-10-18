# quasar-ffmpeg

Quasar 苹果端 libmpv 里的 FFmpeg 源码：FFmpeg n9.0.2（`upstream` 远端，提交 `946fcce0`）的 fork。`main` 上基线之后的每个提交原是 LePips/MPVUI 的一个苹果端 FFmpeg 补丁，提交说明写了出处和用途。

| 规则 | 谁来挡住 |
| --- | --- |
| 这里不编译。quasar-app 的 `iosApp/tool/build_libmpv.sh` 按 `iosApp/tool/quasar_ffmpeg.sh` 里的 `QUASAR_FFMPEG_COMMIT` 取这里的代码，生成一个补丁替换 MPVUI 锁文件里的苹果端 FFmpeg 补丁。改完在这里提交，再到 quasar-app 更新提交号、重编、真机验证，按 quasar-app 的流程审查合入 | 判断 |
| 构建不开 GPL（不加 `--enable-gpl`）。不引入只能按 GPL 用的代码 | quasar-app 的 `build_libmpv.sh` 检查 `CONFIG_GPL 0` |
| 5 个导入提交都取自 LePips/MPVUI；其中 0002、0003、0004 的代码又来自 edde746/MPVKit 的 `b8b922ec`（LGPL-3.0），这些文件按 LGPL-3.0 分发；它之后的版本是 GPL-3.0-only，不再拿。出处和许可见 `quasar/CREDITS.md`；提交说明里写的 `../AVFOUNDATION_CREDITS.md` 指 quasar-mpv 的同名文件 | 判断 |
| quasar-app 钉的每个提交都打 tag `pin/<日期>-<序号>`。rebase、amend 之后旧提交只靠 tag 留住。仓库暂时只在本地，没有远端备份 | 判断 |
| 本文件不进构建（生成补丁时排除）。`VERSION`、`RELEASE` 由 mpvbuild 准备源码时写入，不在这里改 | `build_libmpv.sh` |
| 升级 FFmpeg：本仓库是浅克隆，基线没有父提交。`git fetch --depth=1 upstream <新标签>`，再 `git rebase --onto <新标签的提交> 946fcce0 main`；quasar-app 同时改 `quasar_ffmpeg.sh` 的 `QUASAR_FFMPEG_BASE`，并升级 MPVUI 的 `COMMIT`（或让脚本改写锁文件里 ffmpeg 的 commit 和 version） | 判断 |
