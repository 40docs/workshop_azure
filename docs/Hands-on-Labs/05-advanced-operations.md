# Configuration & Ops

This section covers advanced FortiGate configuration, troubleshooting procedures, and ongoing operational tasks for your connectivity hub.

## On this page
- [Advanced CLI Configuration](#advanced-cli-configuration)
- [Routing & Policy Management](#routing-policy-management)
- [High Availability Testing](#high-availability-testing)
- [Troubleshooting Guide](#troubleshooting-guide)
- [Performance Optimization](#performance-optimization)
- [Operations & Maintenance](#operations-maintenance)

## Advanced CLI Configuration

### FortiGate High Availability Commands

The following CLI configuration was automatically applied during deployment:

```bash
config system ha
set group-name "azure-ha-cluster"
set mode a-p
set hbdev "port3" 50
set ha-mgmt-status enable
ha-direct
```

### Additional HA Configuration

For advanced HA configurations, you can access the FortiGate CLI and apply additional settings:

```bash
# Configure HA heartbeat settings
config system ha
    set heartbeat-interval 2000
    set heartbeat-lost-threshold 6
    set monitor "port1" "port2"
end

# Configure session pickup
config system session-sync
    set sync-packet-balance enable
end
```

### Network Interface Configuration

```bash
# Configure external interface
config system interface
    edit "port1"
        set mode static
        set ip 10.2.2.4/24
        set allowaccess ping https ssh http
        set type physical
        set role wan
    next
end

# Configure internal interface
config system interface
    edit "port2"
        set mode static
        set ip 10.2.3.4/24
        set allowaccess ping https ssh http
        set type physical
        set role lan
    next
end
```

## Routing & Policy Management

### Static Routes

```bash
# Configure default route via external load balancer
config router static
    edit 1
        set dst 0.0.0.0/0
        set gateway 10.2.2.1
        set device "port1"
    next
end

# Configure route to spoke networks
config router static
    edit 2
        set dst 192.168.0.0/16
        set gateway 10.2.3.1
        set device "port2"
    next
end
```

### Firewall Policies

```bash
# Allow outbound traffic from internal to external
config firewall policy
    edit 1
        set name "Internal_to_External"
        set srcintf "port2"
        set dstintf "port1"
        set srcaddr "all"
        set dstaddr "all"
        set action accept
        set schedule "always"
        set service "ALL"
        set nat enable
    next
end

# Allow traffic between spoke networks
config firewall policy
    edit 2
        set name "Spoke_to_Spoke"
        set srcintf "port2"
        set dstintf "port2"
        set srcaddr "all"
        set dstaddr "all"
        set action accept
        set schedule "always"
        set service "ALL"
    next
end
```

## High Availability Testing

### Failover Testing Procedures

1. **Planned Failover Testing**
   ```bash
   # From primary FortiGate CLI
   execute ha failover set 1
   
   # Monitor failover process
   get system ha status
   ```

2. **Heartbeat Monitoring**
   ```bash
   # Check HA heartbeat status
   diagnose sys ha heartbeat-status
   
   # Monitor HA synchronization
   diagnose sys ha status
   ```

3. **Session Synchronization**
   ```bash
   # Check session sync status
   diagnose sys session sync
   
   # View active sessions
   get system session status
   ```

## Troubleshooting Guide

### Common Issues and Solutions

#### HA Cluster Not Forming

**Symptoms:** FortiGates not forming HA cluster

**Troubleshooting Steps:**
```bash
# Check HA configuration
get system ha status

# Verify heartbeat interfaces
diagnose sys ha heartbeat-status

# Check for configuration mismatches
diagnose sys ha checksum cluster
```

**Resolution:**
- Ensure both units have identical configuration
- Verify heartbeat interface connectivity
- Check HA group name and password match

#### Network Connectivity Issues

**Symptoms:** Unable to reach resources through FortiGate

**Troubleshooting Steps:**
```bash
# Check interface status
get system interface physical

# Verify routing table
get router info routing-table all

# Check firewall policy hits
diagnose firewall policy hit
```

#### Performance Issues

**Symptoms:** Slow network performance through FortiGate

**Troubleshooting Steps:**
```bash
# Monitor CPU and memory usage
get system performance status

# Check interface statistics
diagnose hardware deviceinfo nic <interface>

# Monitor session table
get system session status
```

### Debug Commands

```bash
# Enable debug for policy lookup
diagnose debug enable
diagnose debug flow filter clear
diagnose debug flow filter addr <source-ip>
diagnose debug flow trace start 100
diagnose debug flow show function-name enable

# Monitor real-time logs
execute log filter category traffic
execute log display
```

## Performance Optimization

### CPU and Memory Optimization

```bash
# Configure conserve mode thresholds
config system global
    set memory-use-threshold-extreme 95
    set memory-use-threshold-red 88
    set memory-use-threshold-green 82
end

# Optimize session table
config system session
    set session-ttl 3600
end
```

### Network Performance Tuning

```bash
# Enable hardware acceleration (if supported)
config system global
    set hardware-switch-offload enable
end

# Configure interface buffers
config system interface
    edit "port1"
        set estimated-upstream-bandwidth 1000000
        set estimated-downstream-bandwidth 1000000
    next
end
```

### Load Balancer Optimization

- Monitor Azure Load Balancer metrics
- Adjust health probe intervals
- Configure session persistence if needed
- Monitor backend pool health

## Operations & Maintenance

### Regular Maintenance Tasks

#### Daily Tasks
- Monitor HA status and synchronization
- Check system resource utilization
- Review security logs for anomalies
- Verify backup connectivity

#### Weekly Tasks
- Review and analyze traffic patterns
- Update threat intelligence feeds
- Check for firmware updates
- Validate backup procedures

#### Monthly Tasks
- Perform planned failover testing
- Review and update firewall policies
- Analyze performance trends
- Update documentation

### Backup Procedures

```bash
# Create configuration backup
execute backup config management-station <filename>

# Schedule automatic backups
config system auto-script
    edit "daily-backup"
        set interval 86400
        set repeat 0
        set script "execute backup config management-station daily-backup"
    next
end
```

### Monitoring and Alerting

#### Key Metrics to Monitor

1. **System Health**
   - CPU utilization
   - Memory usage
   - Disk space
   - Interface status

2. **HA Status**
   - Cluster synchronization
   - Heartbeat status
   - Configuration consistency

3. **Network Performance**
   - Interface throughput
   - Session count
   - Latency metrics

4. **Security Events**
   - Blocked traffic
   - Intrusion attempts
   - Policy violations

### Integration with Azure Monitor

- Configure FortiGate to send logs to Azure Log Analytics
- Set up Azure Monitor alerts for critical events
- Create custom dashboards for network visibility
- Implement automated response to common issues

---

**Congratulations!** You have successfully deployed and configured a comprehensive Azure connectivity hub with high-availability FortiGate firewalls. Your infrastructure is now ready for production workloads with proper security, monitoring, and operational procedures in place.