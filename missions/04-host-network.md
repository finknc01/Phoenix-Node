# Mission 04 — Alive but Unreachable

## Briefing
PHX-07 is running and local services are healthy, but the monitoring team cannot reach one service from another host.

## Objective
Connect RHEL host-level networking to service behavior: NetworkManager connections, interfaces, addresses, routes, DNS, listening sockets, firewalld, and reachability.

## Build
Run a simple lab service on a high port. Record its bind address, active NetworkManager connection, interface/IP state, routes, resolver state, firewalld zone/rules, and listening socket.

Useful baseline commands include:

```bash
nmcli connection show --active
nmcli device status
ip addr
ip route
ss -lntup
firewall-cmd --get-active-zones
firewall-cmd --list-all
cat /etc/resolv.conf
```

## Deliberate failure
Choose one safe, reversible fault in the disposable lab: bind the service only to loopback, change a lab NetworkManager connection or route, create a lab-only DNS/resolver problem, stop the listener, or block the high port with a reversible firewalld rule.

## Investigation
Trace from application → socket → host policy → interface → route → neighbor/next hop → remote endpoint. Use `nmcli`, `ss`, `ip addr`, `ip route`, `ip neigh`, `ping`, `tracepath`, `dig`/`getent`, `firewall-cmd`, and `tcpdump` where appropriate.

Do not start by changing NetworkManager or firewall configuration. First prove the first broken layer.

## Evidence to save
- expected packet/application path
- active NetworkManager connection and route evidence
- firewalld zone/rule evidence where relevant
- first confirmed-good and first confirmed-bad layer
- before/failure/after validation

## Victory condition
You can distinguish “host is up,” “interface is configured,” “route exists,” “DNS works,” “firewall permits it,” “service is listening,” and “application is reachable” as separate claims.

## Debrief
- Which tests proved transport/application state rather than just ICMP reachability?
- How did NetworkManager configuration differ from the kernel's currently active route/interface state?
- When firewalld was involved, what evidence proved policy—not routing or the application—was the failed layer?
