## obsidian和git同步

`.obsidian` 里面的文件也推荐进入git仓库，除了 `workspace.json` ，记录的是当前标签页状态，没必要随时跟踪。

推荐每个知识库仓库下的 `.gitignore` 文件加上如下几行：

```
.obsidian/workspace.json

.obsidian/workspace-mobile.json

.trash
```
