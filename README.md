# Shaving Tools

## 项目用途

手机硬件与性能评测工具集，包含 SoC 分析、游戏帧率监控、电池续航和相机测试等项目；通过 Android 采集端与桌面可视化工具研究频率、温度、功耗和性能变化。

## 当前开发状态

包含 Android 采集工具和 Web / 桌面展示项目；不同工具独立开发，根脚本只编排 JS 工作区。硬件能力与性能数据需在相应真机、ADB 或采集服务环境验证。

状态核对：2026-10-21。平台验收、已知问题与后续计划见文档入口中的专项记录。

## 目录结构

| 路径 | 用途 |
| --- | --- |
| [`apps/battery-monitor/`](apps/battery-monitor/) | 独立子项目（入口见该目录配置） |
| [`apps/camera-tools/`](apps/camera-tools/) | 独立子项目（入口见该目录配置） |
| [`apps/game-fps-monitor/`](apps/game-fps-monitor/) | 独立子项目（入口见该目录配置） |
| [`apps/soc-analyzer-android/`](apps/soc-analyzer-android/) | 独立子项目（入口见该目录配置） |
| [`apps/soc-analyzer-pc/`](apps/soc-analyzer-pc/) | 独立子项目（入口见该目录配置） |
| [`apps/web/`](apps/web/) | 用户 Web 应用 |
| [`docs/`](docs/) | 产品、架构与开发文档 |
| [`packages/`](packages/) | 共享包与工程配置 |
| [`package.json`](package.json) | 根包管理器、脚本与工作区入口 |
| [`pnpm-workspace.yaml`](pnpm-workspace.yaml) | 工作区与任务编排配置 |
| [`turbo.json`](turbo.json) | 工作区与任务编排配置 |

## 环境要求

Node.js 18+、pnpm 8；Android Studio、JDK、Android SDK 与 ADB（采集端）；桌面应用按其子项目安装依赖。

根工作区声明 `pnpm@8.15.0`。安装对应版本后再运行以下命令；各子项目的 Go、Python、Rust 或移动端依赖单独安装。

## 启动方式

### 1. 获取源码

```bash
git clone https://github.com/Noliravena/shaving-tools.git
cd shaving-tools
```

### 2. 安装工作区依赖

```bash
pnpm install
```

### 3. 配置本地环境

Android 项目在各自目录使用 Gradle / Android Studio。SoC 展示和相机项目默认端口都可能为 3002，选择单个工具运行或调整端口。

账号、API Key、签名文件和本地数据按忽略规则保存在本机；示例中的值需替换为自己的开发配置。

### 4. 启动所需组件

以下命令均从仓库根目录开始；标为“另开终端”的组件需要同时运行。

#### SoC 展示端

```bash
pnpm --dir apps/soc-analyzer-pc dev
```

#### 游戏帧率桌面端（按需另开终端）

```bash
pnpm --dir apps/game-fps-monitor/desktop dev
```

## 常用命令

| 命令（仓库根目录） | 作用 |
| --- | --- |
| `pnpm dev` | 运行根开发脚本；Go / 原生端以启动方式为准 |
| `pnpm build` | 执行已声明工作区的构建 |
| `pnpm lint` | 执行已声明的静态检查 |
| `pnpm test` | 执行已声明的测试 |

命令对应根 `package.json` 中的真实脚本；任务是否覆盖 Go、固件或移动端，取决于各工作区配置。

## 文档与补充说明

- [产品、架构与开发资料](docs/)

- [对应子项目的完整说明](apps/battery-monitor/README.md)

- [对应子项目的完整说明](apps/soc-analyzer-android/README.md)

- [对应子项目的完整说明](apps/soc-analyzer-pc/README.md)

- [对应子项目的完整说明](apps/web/README.md)

[整理前的完整 README 与专题记录](https://github.com/Noliravena/shaving-tools/blob/574dad829d50f071367621b92ad31c5f33125a67/README.md)。该链接固定到整理前的版本，当前启动入口以上文及源码配置为准。
