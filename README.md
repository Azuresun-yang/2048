

# 🚀 部署步骤（GitHub → Cloudflare）

1. **新建 GitHub 仓库**

   * 进入 [GitHub](https://github.com/new)
   * 名字填：`game2048-worker`
   * 创建后，把上面的文件复制进去，commit。

2. **连接到 Cloudflare**

   * 打开 [Cloudflare Dashboard](https://dash.cloudflare.com/)
   * 找到 **Workers & Pages** → **Create Application** → **Workers**
   * 选择 **Connect to Git** → 选你的 `game2048-worker` 仓库。

3. **配置数据库 D1**
   在本地终端或 Cloudflare 控制台执行：

   ```bash
   wrangler d1 create game2048-db
   wrangler d1 execute game2048-db --file=worker/schema.sql
   ```

   把 `database_id` 填进 `wrangler.toml`。

4. **自动部署**
   每次你 push 到 GitHub，Cloudflare 都会自动更新 Worker。

5. **访问接口**
   Worker 部署成功后，会有一个地址，例如：

   ```
   https://game2048.username.workers.dev
   ```

   * 注册账号：`POST /register`
   * 登录：`POST /login`
   * 上传分数：`POST /score`
   * 排行榜：`GET /leaderboard`

---

要不要我帮你写一个 **可以一键 Fork 的 GitHub Gist 链接**（点开就是整个 repo 的 zip 包），这样你不用自己一个个建文件？
