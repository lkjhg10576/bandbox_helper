# BandBox辅助

LRC 歌词推送 + 动态口令（TOTP）账户同步：手机端选歌词或批量导入 otpauth:// 账户，与手环 BandBox 双向同步

> AstroBox 官方插件源收录插件。手机端 AstroBox 的「插件市场」里可直接搜索安装。

## 配套应用

本插件是 **BandBox**（小米手环百宝箱快应用）的手机端配套插件，负责两条链路：

1. **从手机推送歌词**：手机选 `.lrc` 歌词文件 → 插件剥离时间轴与标签 → 推到手环「歌词本」；
2. **动态口令（TOTP）同步**：批量导入 `otpauth://` 账户 → 下发到手环 → 手环本地离线生成 6 位验证码。

> 装插件前请先在手环上装好 BandBox 快应用（包名 `com.lkjhg.bandbox`），插件按包名寻址手环。

## 安装

**方式一（推荐）**：手机 AstroBox → 插件市场 → 搜索「BandBox辅助」→ 安装。

**方式二（手动）**：下载 [`BandBox辅助.abp`](./release/BandBox辅助.abp)，
用手机 AstroBox 的「从本地导入插件」安装。`.abp` 是标准 zip，内容为 manifest.json + plugin.wasm + icon.png。

## 技术信息

- 版本：0.1.2
- API Level：4
- WASI Version：3
- 入口：`plugin.wasm`（QuickJS → wasm，componentize-qjs 编译）

### 权限清单

- `device` —— 读取已连接的手环设备列表
- `interconnect` —— 向手环发送消息（send-qaic-message）
- `register_interconnect_recv` —— 注册接收手环回执（register-interconnect-recv）

## 源码

- 插件源码与构建脚本：https://atomgit.com/gcw_MchqrexB/MiBandBox/tree/main/plugin/bandbox-helper
- 配套快应用：https://atomgit.com/gcw_MchqrexB/MiBandBox
- GitHub 镜像：https://github.com/lkjhg10576/MiBandBox

## 许可

自由、免费、开源。MIT License。
