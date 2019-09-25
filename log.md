与P2P相关的日志

### Net
- 示例:`Net[Software:127.0.0.1/32:Loopback:id=1]`
- 解释:`Net[<网卡描述>:<IP地址>/<IP地址长度>:<网卡类型>:id=<id>]`
- i:由next_available_network_id_=1决定，每次增加1

### Port
- 示例:`Port[2b92330:audio:1:0:local:Net[Npcap:169.254.168.167/32:Ethernet:id=3]]`
- 解释:`Port[<Port对象16进制内存地址>:<content_name>:<component>:<generation>:<type>:Net[Npcap:169.254.168.167/32:Ethernet:id=3]]`
- content_name:video/audio
- component:ICE_CANDIDATE_COMPONENT_RTP=1/ICE_CANDIDATE_COMPONENT_RTCP=2
- generation:由allocator_sessions_的大小决定
- type:LOCAL_PORT_TYPE/STUN_PORT_TYPE/PRFLX_PORT_TYPE/RELAY_PORT_TYPE

### Cand
- 示例:`Cand[:1981477773:1:udp:2122260223:169.254.168.167:58351:local::0:CFW3:2J9WSglwxGhTeLcZi1n+jCo2:3:0:0]`
- 示例:`Cand[:3285959354:1:udp:2122194687:192.168.1.135:58352:local::0:CFW3:2J9WSglwxGhTeLcZi1n+jCo2:4:0:0]`
- 示例:`Cand[:1116980238:1:udp:1685987071:43.224.212.104:4223:stun:192.168.1.135:58352:CFW3:2J9WSglwxGhTeLcZi1n+jCo2:4:0:0]`
- 示例:`Cand[:3723398083:1:udp:41819903:39.97.72.29:50784:relay:43.224.212.104:4223:CFW3:2J9WSglwxGhTeLcZi1n+jCo2:4:0:0]`
- 解释:`Cand[<transport_name>:<foundation>:<component>:<protocol>:<priority>:<IP>:<port>:<type>:<relate_address_IP>:<relate_address_port>:<usename>:<password>:<network_id>:<network_cost>:<generation>]`
- foundation:是由ComputeFoundation计算出来的
- component:见Port中的component
- protocol:UDP_PROTOCOL_NAME/TCP_PROTOCOL_NAME/SSLTCP_PROTOCOL_NAME/TLS_PROTOCOL_NAME
- priority:是由Candidate::GetPriority计算得到的
- usename
- password
- network_id:见Net中的id
- network_cost
- generation:见Port中的generation

### Conn
- 示例:`Conn[b63643f0:audio:Net[rmnet_data0:10.15.25.x/29:Cellular:id=3]:rmibvgOR:1:0:prflx:udp:1.86.42.x:22309->TssKpYW1:1:41885695:relay:udp:39.97.72.x:50171|CRxI|-|0|0|179897693902749183|95]`
- 解释:`Conn[<ToDebugId>:<content_name>:<网卡信息>:<local.id>:<component>:<generation>:<type>:<protocol>:<IP+port>-><remote.id>:<remote.component>:<remote.priority>:<remote.type>:<remote.protocol>:<remote IP+port>|CRxI|-|0|0|179897693902749183|95]`