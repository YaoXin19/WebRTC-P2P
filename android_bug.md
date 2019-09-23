
### 存在问题
#### Android UDP bind失败问题
- 如果频繁开关移动网络，会导致该问题
- 该问题Android端特有的，IOS没有碰到该问题
- 类似问题见https://bugs.chromium.org/p/webrtc/issues/detail?id=4356


### 禁用系统自带的
    // If set to true, any platform-supported network monitoring capability
    // won't be used, and instead networks will only be updated via polling.
    //
    // This only has an effect if a PeerConnection is created with the default
    // PortAllocator implementation.
    bool disable_network_monitor = false;