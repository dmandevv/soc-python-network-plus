# Network Cable Connectors

## Fiber-optic connectors

| Connector | Full name | Mechanism | Notes |
|---|---|---|---|
| LC | Lucent Connector | Snap-in (latch, like a mini RJ45 clip) | Small form-factor, ~half the size of SC. Most common in modern high-density deployments (data centers) |
| SC | Subscriber/Square Connector | Push-pull | Larger than LC, easier to handle by hand, older/still widely deployed |
| ST | Straight Tip | Bayonet-style twist-and-lock | One of the oldest fiber connectors, largely legacy today |
| MT-RJ | Mechanical Transfer-Registered Jack | Snap-in, RJ45-like size | Holds 2 fibers (TX+RX) in one connector. Never reached LC's adoption, mostly legacy |
| MPO | Multi-fiber Push On | Push-pull | High-density: 12 or 24 fibers (scalable to 72) in one ferrule. Used for high-bandwidth data center trunk links (40/100 Gbps uplinks) |

**Industry trend:** twist-lock (ST) → single-fiber push-pull (SC) → compact single-fiber snap-in (LC) → multi-fiber high-density (MPO). MT-RJ was a side-branch compactness attempt that didn't win out over LC.

## Coaxial connectors

| Connector | Mechanism | Common use |
|---|---|---|
| BNC | Bayonet-style twist-and-lock (Bayonet Neill-Concelman) | Professional audio/video, CCTV, lab/testing equipment |
| F-type | Threaded (screw-on) | Satellite/cable TV, broadband internet via cable modems |

## Twisted-pair / copper connectors

| Connector | Full name | Common use |
|---|---|---|
| RJ45 | Registered Jack 45 (8P8C) | Standard Ethernet — twisted-pair cabling (Cat5e/6/etc.) |
| RJ11 | Registered Jack 11 | Analog telephone lines, DSL modem phone-line port. 4/6 position, smaller than RJ45, not interchangeable |

## Rough relative cost (per connector, field-termination — varies by vendor/quantity)

| Connector | Approx. cost |
|---|---|
| ST | $1-3 |
| SC | $1-4 |
| LC | $2-5 |
| MT-RJ | $3-6 |
| MPO | $15-40+ (pre-terminated trunk cables can run much higher) |
