# Testing

- 已执行：`pnpm install --offline`
 结果：失败。原因是当前终端无 TTY，`pnpm` 拒绝直接移除并重建 `node_modules`。
- 已执行：`CI=true pnpm install --offline --no-frozen-lockfile`
 结果：失败。本地 store 缺少 tarball，无法纯离线补齐依赖。
- 已执行：`CI=true pnpm install --no-frozen-lockfile`
 结果：成功。`swagger-ui-dist` 已安装到 `backend/helloworld/web/node_modules`。
- 已执行：`pnpm build`
 结果：成功。构建产物生成，未再出现 `Can't resolve 'swagger-ui-dist'` 报错。
