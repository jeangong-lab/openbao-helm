# Active-only ServiceMonitor selector

When `server.ha.enabled=true`, the default ServiceMonitor scrapes every server pod.
For local tests I restrict it to the active pod:

```yaml
serverTelemetry:
  serviceMonitor:
    enabled: true
    selectors:
      openbao-active: "true"
```

After a leadership transfer the new leader becomes the only target within about 40 seconds.
