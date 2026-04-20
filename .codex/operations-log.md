# Operations Log

- 2026-04-17 17:xx 读取仓库前端配置、`package.json`、`config.ts`，定位报错来自 `.umi/plugin-openapi/openapi.tsx` 对 `swagger-ui-dist` 的直接导入。
- 2026-04-17 17:xx 检查 `pnpm-lock.yaml` 与 `pnpm why swagger-ui-dist`，确认该包仅以间接依赖形式存在。
- 2026-04-17 17:xx 将 `swagger-ui-dist@4.19.1` 声明为项目直接依赖，准备执行本地安装与构建验证。
- 2026-04-17 17:xx 本地离线安装先后因 `pnpm` 非交互保护与缺失 tarball 失败，随后执行 `pnpm install --no-frozen-lockfile` 完成依赖同步与锁文件更新。
- 2026-04-17 17:xx 执行 `pnpm build`，构建成功，原始 `swagger-ui-dist` 缺失错误已消失；记录到若干 peer dependency warning 与 tree-shaker 日志，但未阻塞产物生成。
