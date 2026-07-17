参考 [[Linux systemctl 命令  菜鸟教程#示例2：创建自定义服务]] 

如下演示代码（已数据脱敏）

```
[Unit]
Description=myproject django
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/myproject
ExecStart=/home/ubuntu/myproject/venv/bin/python -m gunicorn myproject.wsgi --workers 2 --bind 127.0.0.1:8000
Restart=always

[Install]
WantedBy=multi-user.target
```

和ai初次提供的样例做了如下优化：
1. 激活虚拟环境，调用虚拟环境下的gunicorn采用更python社区推荐的 `/venv/bin/python -m` 风格。
2. 移除了对 `PATH` 环境变量的修改，没用，还可能有潜在问题。
3. 采用了gunicorn官方文档的更推荐的django项目的写法：`gunicorn myproject.wsgi` ，原样例还要指明 `application` 名字的写法过于老旧了。

以后就可以直接通过 `systemctl status myproject` 来查看这个后台服务了。