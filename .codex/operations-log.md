# Operations Log

- 2026-04-17 17:xx 读取仓库前端配置、`package.json`、`config.ts`，定位报错来自 `.umi/plugin-openapi/openapi.tsx` 对 `swagger-ui-dist` 的直接导入。
- 2026-04-17 17:xx 检查 `pnpm-lock.yaml` 与 `pnpm why swagger-ui-dist`，确认该包仅以间接依赖形式存在。
- 2026-04-17 17:xx 将 `swagger-ui-dist@4.19.1` 声明为项目直接依赖，准备执行本地安装与构建验证。
- 2026-04-17 17:xx 本地离线安装先后因 `pnpm` 非交互保护与缺失 tarball 失败，随后执行 `pnpm install --no-frozen-lockfile` 完成依赖同步与锁文件更新。
- 2026-04-17 17:xx 执行 `pnpm build`，构建成功，原始 `swagger-ui-dist` 缺失错误已消失；记录到若干 peer dependency warning 与 tree-shaker 日志，但未阻塞产物生成。
- 2026-04-20 读取 `backend/helloworld` 的 Ent、配置和依赖，确认数据库方言仅在驱动依赖、空白导入和默认 DSN 处写死为 MySQL。
- 2026-04-20 将后端数据库驱动从 `github.com/go-sql-driver/mysql` 切换为 `github.com/lib/pq`，并把默认配置改为 PostgreSQL。
- 2026-04-20 准备执行 `go mod tidy` 与 `go test ./...`，确认依赖和编译链路在 PostgreSQL 下保持正常。
- 2026-04-20 首次执行 `go mod tidy` 失败，原因是系统默认 `go-build` 与模块缓存目录权限不足。
- 2026-04-20 改用工作区内 `GOCACHE`/`GOMODCACHE` 并联网执行 `go mod tidy`，成功拉取 `github.com/lib/pq` 并同步 `go.sum`。
- 2026-04-20 在工作区缓存配置下执行 `go test ./...` 成功，说明后端在 PostgreSQL 驱动下可正常编译通过。
