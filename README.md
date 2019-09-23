总结一下WebRTC中的P2P

### 概述
1. 所有与P2P相关的源码都在`src/p2p`下
2. WebRTC中的P2P包含的相关技术有dtls/srtp/ice/turn/stun

### ICE/STUN/RELAY
#### STUN与服务端
1. WebRTC向服务端发送Binging包，服务端从该包中获得客户端的外网IP和port，并返回给WebRTC
2. WebRTC向服务端发送Allocate包，用来向服务端申请转发所需的port，申请成功服务端则返回该port
#### STUN与ICE
1. 依据上述1，WebRTC可以生成srflx地址，即外网映射地址
2. 依据上述2，WebRTC可以生成relay地址，即服务中转地址
#### Connection
1. 双方交换ICE信息后，local candidate和remote candidate会构成一个Connection
2. 目前来看，只有host/host, srflx/srflx, relay/relay这三种情况是可以互通的
#### CheckAndPing(或者是PingAndCheck？？？)
1. Connection的连通性检查，包括连接建立阶段和通话过程中两个阶段
2. 通话过程中，strong连接ping间隔为480ms，weak连接ping间隔为48ms
3. 在弱网条件下，经过5s，strong连接将会转换为weak连接，触发disconnected事件；再过10s，触发timeout事件
4. 上述3中，弱网的判定条件为三个：a. writeable; b. receiving; c. connected
5. 该方法循环调用，每次都会对Connections进行排序，选择最优作为当前连接
#### ICE事件
1. disconnected事件对应上述3
2. failed事件代表所有Connection被销毁，但Port依然存在，还可以重连
#### ICE一次收集与持续收集
1. ICE持续收集：WebRTC每2s会获取网卡信息，如果发现有更改，会生成新的ICE，没有completed状态
2. ICE一次收集: WebRTC只收集一次ICE，结束时会有completed状态

