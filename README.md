# 110 CoBuild 首页

[cobuild.110-lab.cn](https://cobuild.110-lab.cn/) 的独立前端源码仓库。

本仓库只包含 CoBuild 品牌介绍首页及应用跳转入口，不包含工作台、内部应用、认证服务或插件源码，也不保存用户数据、服务器凭据与邮箱配置。

## 本地运行

使用 Node.js 24（`.nvmrc` 固定为 24.15.0）和 npm：

```sh
nvm use
npm ci
npm run dev -- --host 127.0.0.1
```

## 构建和验证

```sh
npm run build
npm run test:sites
npm run preview -- --host 127.0.0.1
```

静态站点输出位于 `dist/client/`。构建同时保留 Sites 兼容产物 `dist/server/index.js` 和 `dist/.openai/hosting.json`；当前正式站点由 Caddy 直接提供静态文件，不运行该 Worker。

## 目录

| 路径 | 内容 |
| --- | --- |
| `src/` | React 页面、交互和样式 |
| `public/assets/` | 正式首页使用的品牌图标、背景和协作示意图 |
| `worker/`、`scripts/` | Sites 兼容构建与静态资源路由 |
| `tests/` | 已有路由与构建产物测试 |
| `docs/production-baseline.json` | 20261015-v1 发布产物的 SHA256 与字节数，用于核对导入基线 |
| `docs/deployment.md` | 发布、验收和回滚约束 |

## 版本管理

本次导入对应已发布的 `20261015-v1` 首页，保留原页面及锁定依赖。`package.json` 中的 `0.0.0` 是原工程值，不代表线上发布编号。

后续修改通过分支和 PR 审核，CI 验证构建和已有测试。Git 提交记录源码版本，发布时另外记录对应提交与产物清单。推送 GitHub 不会自动部署；本仓库没有配置生产发布凭据或自动发布任务。

本仓库及品牌素材未授予开源许可。
