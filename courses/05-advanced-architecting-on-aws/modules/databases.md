# Databases & Deployment Patterns

- **Amazon RDS Blue/Green Deployments:** A managed feature that allows you to stage infrastructure changes (engine upgrades, patch updates) on a "Green" staging environment and then switch over to production with minimized downtime.
    - **How it works:**
        - **Blue:** Current production environment.
        - **Green:** Cloned staging environment (logical replica).
        - **Sync:** Uses asynchronous logical replication to keep Green in sync with Blue.
        - **Switchover:** DNS/Endpoint redirection occurs at the managed level, promoting Green to Production.
    - **Key Architect Considerations:**
        - **Retry Logic:** Application code must be prepared for short connection drops during the switchover.
        - **Schema Compatibility:** You can run schema modifications on the Green environment before switchover, but they must be compatible with the Blue environment during replication.
        - **Downtime:** Minimized but usually not strictly zero; always design for connection resiliency.

### Managed Service Failover (Blue/Green)
```text
    [Application]
          | (Read/Write)
          v
    +--------------------------+
    | Blue (Production DB)     | <--- (Logical Replication) --- [Green (Staging DB)]
    +--------------------------+                                (Target Version)
          |
    (During Switchover)
          |
    [Application] --> [Green (Becomes Production)]
```
