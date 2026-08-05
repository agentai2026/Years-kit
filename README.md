# Years-kit

跨平台 Flutter / Dart 音视频播放库镜像。基于 [Predidit/media-kit](https://github.com/Predidit/media-kit) 全量同步，上游来自 [media-kit/media-kit](https://github.com/media-kit/media-kit)。

| | |
| --- | --- |
| 上游仓库 | [Predidit/media-kit](https://github.com/Predidit/media-kit) |
| 同步频率 | 每天北京时间 **00:00** 自动全量同步 |
| 手动同步 | [Actions → Sync Upstream](https://github.com/agentai2026/Years-kit/actions/workflows/sync-upstream.yml) → Run workflow |
| 适用平台 | Windows · Android · Linux · macOS · iOS |

---

## 相对原版的增强

本镜像继承 Predidit 分支的能力：

1. **启发式广告屏蔽**（@0Chencc）— 在 `PlayerConfigure` 中启用后，可自动跳过 HLS 流里插入的 TS 广告片段  
2. **Linux 自带 libmpv2.so** — 不再依赖系统安装的 mpv  
3. **Windows 原生 D3D11** — 零拷贝硬件加速渲染，摆脱 ANGLE  
4. **Linux 三重缓冲** — 模拟 Vulkan 交换链，减轻糟糕 OpenGL 驱动导致的黑屏 / 闪烁  
5. **avbuild FFmpeg 补丁** — 可播放原版 media-kit 播不了、但 [`video_player`](https://pub.dev/packages/video_player) 能播的非标准流（见 [avbuild](https://github.com/wang-bin/avbuild)）  
6. **更新的 mpv** — 二进制体积更小  

---

## 接入方式

在 `pubspec.yaml` 中引用本仓库：

```yaml
dependencies:
  media_kit:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./media_kit
  media_kit_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./media_kit_video
  media_kit_libs_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/universal/media_kit_libs_video

dependency_overrides:
  media_kit:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./media_kit
  media_kit_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./media_kit_video
  media_kit_libs_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/universal/media_kit_libs_video
  media_kit_libs_linux:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/linux/media_kit_libs_linux
  media_kit_libs_ios_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/ios/media_kit_libs_ios_video
  media_kit_libs_android_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/android/media_kit_libs_android_video
  media_kit_libs_windows_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/windows/media_kit_libs_windows_video
  media_kit_libs_macos_video:
    git:
      url: https://github.com/agentai2026/Years-kit.git
      ref: main
      path: ./libs/macos/media_kit_libs_macos_video
```

---

## 仓库说明

- 分支与标签与上游保持一致；本地仅额外保留同步工作流与本说明文档  
- 上游无提交时定时任务仍会执行，有更新则自动合并 / 覆盖对齐  
- 更多 API 与平台细节见原项目：[media-kit](https://github.com/media-kit/media-kit) · [Predidit 分支说明](https://github.com/Predidit/media-kit)
