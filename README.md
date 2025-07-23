# JsonRpc

## 项目简介

RPC（Remote Procedure Call，远程过程调用）是一种可以让你像调用本地方法一样，去调用远程服务器上的方法和服务，而无需关心底层网络通信的细节。RPC 支持多种网络协议（如 HTTP、TCP、UDP 等），在 TCP/IP 网络四层模型中跨越了传输层和应用层。简而言之，RPC 就是让远程方法调用像本地方法调用一样简单。

一个完整的 RPC 通信框架通常包括以下内容：
- 序列化协议
- 通信协议
- 连接复用
- 服务注册
- 服务发现
- 服务订阅和通知
- 负载均衡
- 服务监控
- 同步调用
- 异步调用

## 项目特性

本项目基于 **C++**、**JsonCpp**、**muduo 网络库** 实现了一个简单易用的 RPC 通信框架。即使是不懂网络的开发者也能快速上手。本框架实现了如下功能设计：
- 同步调用
- 异步 callback 调用
- 异步 future 调用
- 服务注册/发现
- 服务上下线
- 发布/订阅机制

## 技术选型

1. **RPC 实现方案**  
   - 常规方案：client和server继承公共接口，使用 IDL（接口描述语言），根据 IDL 生成 C++/Java 代码。常见的 Protobuf、JSON 可定义 IDL 接口，自动生成代码。该方式需要编写代码生成器，难度较高。
   - 本项目方案：实现一个远程调用接口 `call`，通过传入函数名参数来调用 RPC 接口，简化开发流程。

2. **参数和返回值的映射**  
   - 采用 JSON 类型，设计好参数和返回值的协议即可。相比 protobuf 反射、C++ 模板类型萃取等方式，学习成本更低。

3. **网络通信层**  
   - 使用 muduo 网络库，学习和开发成本低，适合项目需求。

4. **序列化/反序列化**  
   - 使用 JsonCpp 进行 JSON 的序列化与反序列化。

## 环境搭建

### 安装 JsonCpp

```bash
sudo apt-get install libjsoncpp-dev
```

### 安装 Muduo

1. 下载源码
   ```bash
   git clone https://github.com/chenshuo/muduo.git
   ```

2. 安装依赖
   ```bash
   sudo apt-get install libz-dev libboost-all-dev
   ```

3. 编译安装
   ```bash
   unzip muduo-master.zip
   cd muduo-master
   ./build.sh
   ./build.sh install
   ```

## 参考资料

- [Muduo 网络库](https://github.com/chenshuo/muduo)
- [JsonCpp](https://github.com/open-source-parsers/jsoncpp)
- [比特就业课](#)

## 版权说明

本项目仅用于学习和交流，欢迎提出建议和改进！
