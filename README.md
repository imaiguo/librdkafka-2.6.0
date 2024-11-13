
# librdkafka

## 依赖

1. zlib is installed automatically from NuGet,
   but probably requires the NuGet VS extension.

2. OpenSSL-win32 must be installed in C:\OpenSSL-win32 and C:\OpenSSL-Win64


## Build with MSVC

### Release Build

```bash
> cmd
> "C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvars64.bat"
> cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=D:\devtools\librdkafka-2.6.0
> ninja & ninja install
```

### Debug Build

```bash
> cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=D:\devtools\librdkafka-2.6.0\debug
```

## kafka操作

Docker中执行

```bash
>
> # 1. 创建一个主题 quickstartevents
> sudo docker exec -it 434 /opt/kafka/bin/kafka-topics.sh --create --topic quickstartevents --bootstrap-server localhost:9092
> # 1.1 查看主题
> sudo docker exec -it 434 /opt/kafka/bin/kafka-topics.sh --describe --topic quickstartevents --bootstrap-server localhost:9092
> # 2 写点内容事件到主题中
> sudo docker exec -it 434 /opt/kafka/bin/kafka-console-producer.sh --topic quickstartevents --bootstrap-server localhost:9092
> # You can stop the producer client with Ctrl-C at any time.
> # 3 从主题中读取内容事件
> sudo docker exec -it 434 /opt/kafka/bin/kafka-console-consumer.sh --topic quickstartevents --from-beginning --bootstrap-server localhost:9092
> # You can stop the consumer client with Ctrl-C at any time.
> # 4 停止kafka环境
> # 4.1 Stop the producer and consumer clients with Ctrl-C, if you haven't done so already.
> # 4.2 清理kafka所有数据
> sudo docker exec -it 434 rm -rf /tmp/kraft-combined-logs
> # 5 查看主题列表
> sudo docker exec -it 434 /opt/kafka/bin/kafka-topics.sh --list --bootstrap-server localhost:9092 
> # 6 删除主题列表
> sudo docker exec -it 434 /opt/kafka/bin/kafka-topics.sh --delete --topic quickstartevents --bootstrap-server localhost:9092 
```
