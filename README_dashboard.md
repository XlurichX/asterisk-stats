# Dashboard Metrics Description

## Memory

- **Resident Memory (MB)** – Live memory used by the process.
- **Virtual Memory (MB)** – Total virtual memory used by the process.

## CPU

- **Total CPU Time (s)** – Total CPU time consumed by the process in seconds.

## Garbage Collection

- **GC Collections (by Generation)** – Number of garbage collections per generation:
  - **Gen 0** – Short-lived objects.
  - **Gen 1** – Medium-lived objects.
  - **Gen 2** – Long-lived objects (e.g., singletons).

## File Descriptors

- **Open File Descriptors** – Number of open files by the process.

## Asterisk Peer Status

- BarGauge showing peer status:
  - **1** — active
  - **0** — inactive
- Legend displays peer name and protocol.

## Asterisk Channels

- **Active Channels** – Number of currently active channels by type (PJSIP, IAX2).
- **Total Created Channels** – Total number of channels created since process start.

