# Mission 04 — Alive but Unreachable

## Briefing
PHX-07 is running and local services are healthy, but the monitoring team cannot reach one service from another host.

## Objective
Connect host-level networking to service behavior: interfaces, addresses, routes, DNS, listening sockets, and firewall state.

## Build
Run a simple lab service on a high port. Record its bind address, local route, resolver state, and listening socket.

## Deliberate failure
Choose one safe fault in a VM or namespace: bind the service only to loopback, remove a lab route, change a lab DNS record/resolver, or block the high port with a reversible firewall rule.

## Investigation
Trace from application to socket to interface to route. Use `ss`, `ip addr`, `ip route`, `ping`, `dig`/`resolvectl`, and packet capture when needed.

## Evidence to save
- expected packet path
- first confirmed-good and first confirmed-bad layer
- socket and route evidence

## Victory condition
You can distinguish “host is up,” “IP works,” “DNS works,” and “application is reachable” as separate claims.

## Debrief
Which tests proved transport/application state rather than just ICMP reachability?
