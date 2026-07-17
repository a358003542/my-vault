遇到 403 错误可能是静态文件的权限问题。

安全这块ai给的建议还是很稳妥的，记录下来参考下。(数据已脱敏)

```
sudo chown -R ubuntu:www-data /var/www/myproject
sudo chmod -R 755 /var/www/myproject
```

说明如下：

1. 静态文件不要和代码放在同一目录下（这设置下 `STATIC_ROOT` 很容易就实现了）。
2. linux下的nginx默认使用 www-data 用户组，所有的静态文件都设置为用户是ubuntu，用户组是www-data。
3. ubuntu权限7可写，其他用户组和其他用户只可读。

