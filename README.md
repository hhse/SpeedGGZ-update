# SpeedGG-Z 版本信息

这个仓库只存放 App 内「检查更新」读取的版本元数据，不含源码。App 侧优先从 CDN 读取：

```
https://cdn.jsdelivr.net/gh/hhse/SpeedGGZ-update@main/version.json
```

CDN 读取失败时会退回 `raw.githubusercontent.com` 上的同一文件。

## 发新版本时怎么改

只改 `version.json`：

| 字段 | 说明 |
|---|---|
| `version` | 最新版本号，必须和 `MARKETING_VERSION` 一致（`v` 前缀可有可无） |
| `notes` | 更新说明，会显示在 App 的更新弹窗里（可换行，建议控制在几百字内） |
| `url` | 可选。填了按钮显示「去下载」并跳到这个地址；不填则按钮显示「打开公众号」，跳到公众号链接 |
| `publishedAt` | 可选，仅作记录，App 不读取 |

改完提交到 `main` 即可。jsDelivr 会缓存，生效通常需要几分钟；App 侧的原始地址兜底不受缓存影响。

## 注意

- `version` 必须大于用户当前版本（例如用户 3.9.2、这里写 3.9.3）才会提示；相等时显示「已是最新版本」。
- 这里的版本号同时也是「最新可用版本」的对外声明，发版时别忘记同步更新。
