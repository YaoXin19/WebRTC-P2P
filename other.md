### 网卡类型判断
```
AdapterType GetAdapterTypeFromName(const char* network_name);
```


### 创建Port和Cand
```
void JsepTransportController::MaybeStartGathering();
void P2PTransportChannel::MaybeStartGathering();
void BasicPortAllocatorSession::StartGettingPorts();
void BasicPortAllocatorSession::GetPortConfigurations();
void BasicPortAllocatorSession::ConfigReady(PortConfiguration* config);
void BasicPortAllocatorSession::OnConfigReady(PortConfiguration* config);
void BasicPortAllocatorSession::OnAllocate();
void BasicPortAllocatorSession::DoAllocate(bool disable_equivalent);
void AllocationSequence::Start();
void AllocationSequence::CreateUDPPorts();
```

```
void BasicPortAllocatorSession::StartGettingPorts();
void BasicPortAllocatorSession::OnNetworksChanged();
```
```
void BasicPortAllocatorSession::OnMessage(rtc::Message* message) {
  switch (message->message_id) {
    case MSG_CONFIG_START:
      GetPortConfigurations();
      break;
    case MSG_CONFIG_READY:
      OnConfigReady(static_cast<PortConfiguration*>(message->pdata));
      break;
    case MSG_ALLOCATE:
      OnAllocate();
      break;
    case MSG_SEQUENCEOBJECTS_CREATED:
      OnAllocationSequenceObjectsCreated();
      break;
    case MSG_CONFIG_STOP:
      OnConfigStop();
      break;
    default:
      RTC_NOTREACHED();
  }
}
```
