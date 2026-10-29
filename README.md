# 明点服务器管理系统 · 发布

这里是[明点服务器管理系统](https://github.com/12312bg/mdbmc)（MDBMC）的发布仓库，只存放编译好的版本，源代码在 [12312bg/mdbmc](https://github.com/12312bg/mdbmc)。

## 下载

在 [Releases](https://github.com/12312bg/mdbmc-release/releases/latest) 中下载最新版本：

| 文件 | 说明 |
| --- | --- |
| `mdbmc-amd64-installer.exe` | 安装包（含 Java 运行环境），推荐 |
| `mdbmc-portable-windows-amd64.zip` | 免安装版，解压后运行 `mdbmc.exe` |
| `latest.json`、`latest.json.sig` | 软件在线更新使用的更新清单及其签名 |
| `SHA256SUMS.txt` | 各文件的 SHA-256 校验值 |

系统要求：Windows 10 / 11 或 Windows Server 2016 及以上（64 位），需要 WebView2 Runtime（Windows 10/11 一般自带，安装包会自动安装）。

## 在线更新

已安装的软件会从本仓库的最新 Release 自动检查新版本（“系统设置 → 软件更新”可调整检查间隔、代理和更新源），管理员确认后自动下载、校验并安装。

- 每个 Release 中的 `latest.json` 记录版本号、更新说明和安装包的 SHA-256，并由发布流程用私钥签名（`latest.json.sig`）；软件内置公钥，签名或校验值不符的更新会被拒绝。
- 预发布版本（标签带“-”，如 `v1.2.0-beta.1`）不会推送给已安装的软件。
- 不能访问 GitHub 的环境，可以把某个 Release 的文件放到内网 Web 服务器上，按以下结构存放，并在软件中把更新源改为 `<更新源>`：

  ```
  <更新源>/latest/download/latest.json
  <更新源>/latest/download/latest.json.sig
  <更新源>/download/<标签>/mdbmc-amd64-installer.exe
  <更新源>/download/<标签>/mdbmc-portable-windows-amd64.zip
  ```

## 发布方式

Release 由 mdbmc 仓库的 GitHub Actions 在推送 `v*` 标签后自动创建，请勿手动修改或删除 Release 中的 `latest.json` 和 `latest.json.sig`。发布步骤见 mdbmc 仓库 README 的“发布新版本”一节。
