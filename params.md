与P2P相关的参数

### 系统NetworkMonitor
```
    // If set to true, any platform-supported network monitoring capability
    // won't be used, and instead networks will only be updated via polling.
    //
    // This only has an effect if a PeerConnection is created with the default
    // PortAllocator implementation.
    bool disable_network_monitor = false;
```


```
// src/sdk/android/src/jni/pc/peer_connection_factory.cc


```