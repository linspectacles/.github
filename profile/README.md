# LinSpectacles

**Focused Linux inspection tools for people who want to see what the system is actually reporting.**

LinSpectacles is an open-source family of graphical Linux inspectors built around a simple idea: **one subsystem, one focused tool, one honest view of the underlying data**.

Rather than hiding Linux behind generic dashboards, LinSpectacles gives familiar system interfaces a clear graphical face — while preserving their native terminology, provenance, and boundaries.

The project includes standalone inspectors, live monitoring tools, and the **LinSpectacles Hub**, which brings them together without making the individual applets dependent on the Hub.

---

## Applets

Each LinSpectacles applet is independently useful and keeps its own Linux subsystem, acquisition sources and scope boundaries explicit.

- **[Autostart Inspector](https://github.com/linspectacles/autostart-inspector)** — Inventories configured automatic-start and scheduled-launch entries across systemd, XDG autostart, cron, anacron and supported legacy mechanisms.
- **[Block Devices](https://github.com/linspectacles/block-devices)** — Inspects Linux block-device topology, geometry and mappings from sysfs, with explicit selected-device signature inspection.
- **[Boot Loaders](https://github.com/linspectacles/boot-loaders)** — Structures boot-loader, ESP and EFI state reported by `bootctl`, with optional narrow privileged visibility.
- **[Boot Timing](https://github.com/linspectacles/boot-timing)** — Analyses systemd boot timing, per-unit durations, boot phases, milestones and critical paths, with `boot.log` as supporting evidence.
- **[Cgroups Inspector](https://github.com/linspectacles/cgroups-inspector)** — Browses the cgroup v2 hierarchy, membership, controllers, limits, accounting, events and pressure without becoming a cgroup-management tool.
- **[Coredumps Inspector](https://github.com/linspectacles/coredumps-inspector)** — Inspects coredump records and metadata visible through `systemd-coredump` / `coredumpctl`.
- **[Crypto Registry](https://github.com/linspectacles/crypto-registry)** — Exposes the Linux Kernel Crypto API registry reported by `/proc/crypto`, preserving separate registered implementations and their metadata.
- **[D-Bus Inspector](https://github.com/linspectacles/dbus-inspector)** — Explores system and session D-Bus names, connections, object paths, interfaces and declared members without activating services or invoking methods.
- **[Environment Variables](https://github.com/linspectacles/environment-variables)** — Inspects the environment inherited by the LinSpectacles process, including clearer presentation of path-like values and optional sensitive-value hiding.
- **[Files Handles](https://github.com/linspectacles/files-handles)** — Reports global Linux file-description and inode-allocation state from procfs.
- **[Hardware Topology](https://github.com/linspectacles/hardware-topology)** — Maps CPU/cache locality, PCI devices, NUMA structure, IOMMU groups and kernel-reported CPU vulnerability state.
- **[Initramfs Inspector](https://github.com/linspectacles/initramfs-inspector)** — Discovers installed initramfs/initrd images, identifies image properties and can explicitly inspect contents through supported initramfs tooling.
- **[Installed Software](https://github.com/linspectacles/installed-software)** — Explicitly scans distribution packages, Flatpak applications, Snap packages and AppImages discovered in configured folders.
- **[Interrupts Inspector](https://github.com/linspectacles/interrupts-inspector)** — Inspects hardware IRQ routing and SoftIRQ counters with per-CPU distribution and available kernel/device context.
- **[IPC Inspector](https://github.com/linspectacles/ipc-inspector)** — Browses Linux pipes, FIFOs, Unix-domain sockets, POSIX message queues and System V IPC objects.
- **[Journal Inspector](https://github.com/linspectacles/journal-inspector)** — Provides structured Journal Entries and Boot List inventories with explicit acquisition controls, filtering and retained journal metadata.
- **[Kernel Modules](https://github.com/linspectacles/kernel-modules)** — Inspects loaded kernel modules using `/proc/modules`, `modinfo` and sysfs, including relationships, parameters, taint context and selected-module symbols.
- **[Kernel Pressure](https://github.com/linspectacles/kernel-pressure)** — Presents Linux Pressure Stall Information for CPU, memory and I/O directly from the kernel PSI interfaces.
- **[Kernel Ring Buffer](https://github.com/linspectacles/kernel-ring-buffer)** — Inspects the native kernel printk ring buffer from `/dev/kmsg`, preserving record fields that formatted output can hide.
- **[Kernel Tunables](https://github.com/linspectacles/kernel-tunables)** — Safely browses the runtime kernel parameter namespace exposed through `/proc/sys` without modifying tunables.
- **[Login Inspector](https://github.com/linspectacles/login-inspector)** — Inspects the current `systemd-logind` model of sessions, users, seats and manager properties.
- **[Mounted Filesystems](https://github.com/linspectacles/mounted-filesystems)** — Inventories mounted filesystems from `/proc/self/mountinfo`, adds capacity data and exposes supported ext4, XFS and Btrfs structural details on demand.
- **[Namespace Inspector](https://github.com/linspectacles/namespace-inspector)** — Browses Linux namespace identities and process membership using procfs references and nsfs relationship ioctls.
- **[Path Inspector](https://github.com/linspectacles/path-inspector)** — Inspects a user-selected filesystem path through separate Access, Integrity and Usage views with explicit recursive operations.
- **[Power and Thermal Inspector](https://github.com/linspectacles/power-thermal-inspector)** — Provides point-in-time inspection of thermal zones, cooling devices, CPU-frequency policies, power supplies and kernel power-cap domains.
- **[Python Packages](https://github.com/linspectacles/python-packages)** — Explicitly inventories Python distributions visible to the running environment through `importlib.metadata`.
- **[Resolver Inspector](https://github.com/linspectacles/resolver-inspector)** — Inspects Linux name-resolution configuration and state through active systemd-resolved data or conventional resolver/NSS fallback context.
- **[Resource Monitor](https://github.com/linspectacles/linux-resmon)** — Live CPU, memory, disk and network monitoring with Linux-native process, service, handle, memory, storage and socket views plus a parallel TUI.
- **[Scheduler Inspector](https://github.com/linspectacles/scheduler-inspector)** — Inspects per-thread scheduling policy and affinity, scheduler accounting, per-CPU schedstat state, scheduling domains and global scheduler context.
- **[SELinux Inspector](https://github.com/linspectacles/selinux-inspector)** — Inspects SELinux status, contexts, policy inventories, recent denials and file-context expectations with optional narrow helper-backed visibility.
- **[Systemd Inspector](https://github.com/linspectacles/systemd-inspector)** — Inspects runtime units and unit files across system and user managers, including relationships, provenance, cgroups, runtime details and systemd security exposure data.
- **[Timekeeping Inspector](https://github.com/linspectacles/timekeeping-inspector)** — Inspects Linux clocks, the active kernel clocksource, synchronization/time-discipline state and RTC devices.

---


## Design principles

### Specialist tools first

LinSpectacles prefers a collection of focused inspectors over one enormous application that tries to explain every Linux subsystem at once.

A good applet should be able to answer:

> **What source am I inspecting, and what does that source actually report?**

### Linux-native semantics

The project may take inspiration from tools on other operating systems, but it does not rename Linux concepts simply to imitate them.

Linux data should remain recognisably Linux.

### Read-only by default

Inspectors are designed to observe rather than administer.

Where privileged access is genuinely useful, it should be:

- explicit
- narrow
- read-only
- visibly identified
- implemented through a helper rather than by elevating the GUI

### Provenance matters

Metadata should make it clear where information came from — `/proc`, `/sys`, systemd, the journal, a kernel interface, a package database, or another declared source.

### No hidden scanning

Expensive or privileged inspection should happen because the user asked for it, not because a dashboard silently decided to probe the machine.

### Consistency without sameness

LinSpectacles applets share a common interaction language — inventory, search/filtering, Metadata Details, keyboard navigation, Sources, Options, and export — while still allowing each subsystem to have the specialist controls it genuinely needs.

---

## LinSpectacles Hub

The **LinSpectacles Hub** is the optional host/workbench for the applet family.

The applets remain independently useful. The Hub adds shared navigation and optional modules without turning standalone inspectors into tightly coupled components.

Hub modules include capabilities such as:

- **Applet Organizer**
- **Boot Environment**
- **Encyclopedia & What’s This?**
- **Privileged Helpers**
- **System Identity**
- **System Pulse**

The architectural rule is simple:

> **Inspectors inspect Linux. Hub modules enhance the workbench.**

---

## Project direction

LinSpectacles is gradually building a broad Linux inspection toolkit while keeping subsystem boundaries explicit.

Current and future work explores areas such as:

- deeper filesystem and block-device inspection
- process and kernel event tracing
- access and permission analysis
- file verification and integrity evidence
- richer cross-inspector relationships inside the Hub

The goal is not to reproduce another platform’s utility collection one-for-one.

The goal is to build the inspection toolkit that **Linux itself naturally suggests**.

---

## Repositories

Browse the organisation for individual applets, Hub components, experiments and source releases:

**https://github.com/linspectacles/**

Each repository documents its own current status, dependencies, version and usage.

---

## Philosophy in one line

**Expose the subsystem. Preserve the evidence. Keep the tool focused.**
