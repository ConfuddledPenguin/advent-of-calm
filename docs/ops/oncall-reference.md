# On-Call Quick Reference

**Architecture:** 
**Generated:** 

## Service Contacts

| Service | Owner | On-Call Channel | Tier |
|---------|-------|-----------------|------|
| Load Balancer | platform-team | #oncall-platform | tier-1 |
| API Gateway Instance 1 | platform-team | #oncall-platform | tier-1 |
| API Gateway Instance 2 | platform-team | #oncall-platform | tier-1 |
| Order Service | order-team | #oncall-orders | tier-1 |
| Inventory Service | inventory-team | #oncall-inventory | tier-2 |
| Payment Service | payments-team | #oncall-payments | tier-1 |
| Order Processing Queue |  |  |  |

## Database Contacts

| Database | DBA Contact | Backup Schedule | Restore Time |
|----------|-------------|-----------------|--------------|
| Order Database Primary | #dba-team | daily at 02:00 UTC | 30 minutes |
| Order Database Replica | #dba-team | synced from primary | 5 minutes (failover promotion) |
| Inventory Database | #dba-team | daily at 03:00 UTC | 45 minutes |

## Critical Flows & Business Impact

### Customer Order Processing

- **Business Impact:** Customers cannot complete purchases - direct revenue loss
- **SLA:** 99.9% availability, 30s p99 latency
- **Degraded Behavior:** Orders queue in message broker; processed when service recovers
- **Customer Communication:** Display &#x27;Order processing delayed&#x27; message

**Flow Path:**
0. customer-interacts-with-gateway
1. gateway-to-order-service
2. order-service-to-inventory-service
3. order-service-to-payment-service

---

### Inventory Stock Check

- **Business Impact:** Stock levels may be inaccurate - risk of overselling
- **SLA:** 99.5% availability, 500ms p99 latency
- **Degraded Behavior:** Fall back to cached inventory; flag orders for manual review
- **Customer Communication:** Display &#x27;Stock availability being confirmed&#x27;

**Flow Path:**
0. admin-interacts-with-gateway
1. gateway-to-inventory-service
2. inventory-service-to-inventory-db
3. inventory-service-to-inventory-db
4. gateway-to-inventory-service

---


## Monitoring Links

| Resource | Link |
|----------|------|
| Grafana Dashboard | https://grafana.example.com/d/ecommerce-overview |
| Kibana Logs | https://kibana.example.com/app/discover#/ecommerce-* |
| PagerDuty | https://pagerduty.example.com/services/ECOMMERCE |
| Status Page | https://status.example.com |

## Escalation Matrix

| Tier | Response Time | Escalation Path |
|------|---------------|-----------------|
| tier-1 | 15 minutes | Page immediately, all-hands |
| tier-2 | 30 minutes | Page on-call, notify manager |
| tier-3 | 2 hours | Slack notification, next business day OK |