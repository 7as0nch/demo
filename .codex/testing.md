# Testing

- 已执行：`go mod tidy`
 结果：首次失败。默认缓存目录无权限且沙箱网络受限。
- 已执行：`GOCACHE=D:\workspace\goproject\my\demo\.gocache GOMODCACHE=D:\workspace\goproject\my\demo\.gomodcache go mod tidy`
 结果：成功。已下载 `github.com/lib/pq` 并更新 `backend/helloworld/go.sum`。
- 已执行：`GOCACHE=D:\workspace\goproject\my\demo\.gocache GOMODCACHE=D:\workspace\goproject\my\demo\.gomodcache go test ./...`
 结果：成功。后端所有包通过测试阶段编译检查。
