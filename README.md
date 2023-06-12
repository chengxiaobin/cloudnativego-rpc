# cloudnativego-rpc
1、包管理问题（特指作为server和client依赖的keyvalue包）的解决办法如下：
├── moduledemo
│   ├── go.mod
│   └── main.go
└── mypackage
    ├── go.mod
    └── mypackage.go
 1.1、mypackage内运行go mod init $(包名)
 1.2、在moduledemo/main.go中按如下方式导入：
      import (
        "fmt"
        "mypackage"
      )
 1.3、moduledemo/go.mod中按如下方式指定使用相对路径来寻找mypackage这个包：
      replace "mypackage" => "../mypackage"
      
 2、简单解决go出现大量 undefined
      运行go build，生成二进制可执行文件，程序运行正常
