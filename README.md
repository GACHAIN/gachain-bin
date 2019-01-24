# 主程序go-gachain启动命令和相关参数说明

下载地址：[https://github.com/GACHAIN/gachain-bin/releases](https://github.com/GACHAIN/gachain-bin/releases)

> Mac系统和Linux系统下载地址需将名称修改为`go-gachain`

全局标志（在所有命令中有效）：

    --config string     配置文件config.toml的路径
    -h, --help          详情帮助

## 命令：

- config - 从默认值生成由参数path指定的配置文件的内容。可以使用如下可用标志来更改整个缺省生成的配置值：

```
    --centSecret string       消息通知密码 (默认 "127.0.0.1")
    --centUrl string          消息通知地址 (默认 "127.0.0.1")
    --dataDir string          工作目录 (默认 cwd/gachain-data)
    --dbHost string           数据库地址 (默认 "127.0.0.1")
    --dbName string           数据库名称 (默认 "gachain")
    --dbPassword string       数据库密码 (默认 "gachain")
    --dbPort int              数据库端口 (默认 5432)
    --dbUser string           数据库用户名 (默认 "postgres")
    --firstBlock string       第一个区块的路径 (默认 dataDir/1block)
    -h, --help                帮助
    --httpHost string         节点的http地址 (默认 "127.0.0.1")
    --httpPort int            节点的http端口 (默认 7079)
    --keysDir string          密钥存储路径 (默认 dataDir)
    --lock string             节点进程锁文件 (默认 dataDir/go-gachain.lock)
    --logFormat string        日志格式， text|json (默认 "text")
    --logLevel string         日志级别 (DEBUG | INFO | WARN | ERROR) (默认 "ERROR")
    --logTo string            输出日志路径 stdout|(filename)|syslog (默认 "stdout")
    --mpgt int                页面生成的最大时长（毫秒ms）(默认 1000)
    --nodesAddr strings       区块链的下载地址列表
    --path string             配置文件的路径 (默认 dataDir/config.toml)
    --pid string              节点进程号文件名称 (默认 dataDir/go-gachain.pid)

    --statsdHost string       StatsD地址 (默认 "127.0.0.1")
    --statsdName string       StatsD名称 (默认 "gachain")
    --statsdPort int          StatsD端口 (默认 8125)
    --syslogFacility string   日志工具 (默认 "kern")
    --syslogTag string        日志标签 (默认 "go-gachain")
    --tcpHost string          节点TCP地址 (默认 "127.0.0.1")
    --tcpPort int             节点TCP端口 (默认 7078)
    --tempDir string          临时目录 (默认操作系统临时目录)
    --tls                     是否启用https，默认false
    --tls-cert string         https证书路径
    --tls-key string          https证书密钥路径
    --tmovFrom string         通证转移发送地址
    --tmovHost string         通证转移主机地址
    --tmovPort int            通证转移主机端口
    --tmovPw string           通证转移主机密码
    --tmovSubj string         通证转移主题
    --tmovTo string           通证转移接收地址
    --tmovUser string         通证转移发送人
```

- generateKeys - 生成密钥对，包括当前节点的节点公钥私钥和公钥私钥

- generateFirstBlock - 生成第一个区块

```
    -- stopNetworkCert   用于停止节点网络的完整证书链
    -- test              如果是 true 表示启动测试链
    -- private           如果是 true 表示启动私链
```

- initDatabase - 初始化数据库

- rollback - 将块回滚到特定块。标志有：

```
    --blockId    将链回滚至某个区块高度 (默认回滚至区块高度 1)
```

- start - 启动节点

```
    -- testRollBack 如果是 true 启动一组特殊守护进程
    -- funcBench    禁用一些内置函数的权限检查
```

- stopNetwork - 停止节点

```
    --stopNetworkCert   停止节点网络的证书路径
    --addr              需要停止的节点数组
```

默认的参数启动顺序：

```
./go-gachain  config
./go-gachain  generateKeys
./go-gachain  generateFirstBlock
./go-gachain  initDatabase
./go-gachain  start
```
