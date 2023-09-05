# 磁盘空间不足
```
Build Error: go build -o /export/server/test/phw/gamed -gcflags all=-N -l .
# im_server/gamed
/usr/local/go/pkg/tool/linux_amd64/link: running gcc failed: exit status 1
collect2: 错误：ld 返回 1 (exit status 2)
```

# VS Code 配置
```
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "gamed",
            "type": "go",
            "request": "launch",
            "program": "/export/home/pei/workspace/im_server/gamed/",  // 工作目录
            "cwd": "/export/server/test/peihongwei/",
            "output": "/export/server/test/peihongwei/gamed",
            "asRoot": true,                                            // root 权限
            "console": "integratedTerminal",                           // root 权限
            "env": {
                "GOPATH": "/export/home/pei/workspace/im_server/gamed/", //调整为实际设置目录
                "GOROOT": "/usr/local/go",  //调整为实际设置目录
            },
            "args": [                                                  // 程序实参
                "/export/server/test/peihongwei/conf/gamed.conf.json"
            ]
        }
    ]
}
```