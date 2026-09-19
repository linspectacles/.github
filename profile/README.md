# LinSpectacles

**Focused Linux inspection tools for people who want to see what the system is actually reporting.**

LinSpectacles is an open-source family of graphical Linux inspectors built around a simple idea: **one subsystem, one focused tool, one honest view of the underlying data**.

Rather than hiding Linux behind generic dashboards, LinSpectacles gives familiar system interfaces a clear graphical face — while preserving their native terminology, provenance, and boundaries.

The project includes standalone inspectors, live monitoring tools, and the **LinSpectacles Suite**, which brings them together without making the individual applets dependent on the Suite.

---

## Featured inspectors

### Systemd Inspector

A deep graphical inspector for `systemctl` and the systemd manager.

- Runtime Units and Unit Files
- System and User manager scopes
- Unit state, load state, dependencies, ordering and reverse relationships
- Unit-file provenance and configuration
- Service runtime and outcome information
- Timer, path, slice, scope and other unit-specific details
- Cgroup, resource and sandbox context

Systemd Inspector is designed to expose what systemd already knows without turning that information into a simplified or invented model.

---

### Resource Monitor

A Linux-native live resource monitor for CPU, memory, disk and network activity.

- Processes and services
- Associated file handles and mapped modules
- Physical-memory and per-process memory detail
- Disk activity and storage devices
- TCP connections, UDP endpoints and listening/bound ports
- GUI and TUI front ends
- Optional, visibly provenance-marked privileged inspection

Its design takes inspiration from Windows Resmon.exe while keeping Linux concepts such as RSS, PSS, USS, cgroups, `/proc`, sockets and device statistics intact.

---

### Hardware Topology

A structural view of how the machine is put together.

- CPU packages, cores and logical CPUs
- Cache topology
- PCI devices
- NUMA nodes
- IOMMU groups

Hardware Topology focuses on relationships, making it easier to understand how processors, memory domains and devices connect.

---

### Cgroups Inspector

A read-only cgroup v2-first browser for the Linux control-group hierarchy.

- Hierarchical cgroup tree
- Processes and threads
- Available and enabled controllers
- CPU, memory and PID limits
- `cgroup.stat` descendant information
- Raw and interpreted controller values
- Source-aware metadata

It is intended to make the cgroup filesystem understandable without hiding its actual kernel semantics.

---

### Scheduler Inspector

A focused view of the Linux CPU scheduler.

- Threads
- CPUs
- Scheduling domains
- Scheduler policy and attributes
- CPU affinity
- Scheduler statistics and details

Scheduler Inspector combines kernel and `/proc` scheduler information into a navigable read-only tool.

---

### Interrupts Inspector

A graphical view of hardware interrupts and SoftIRQ activity.

- Hardware IRQ inventory
- SoftIRQ activity by CPU
- IRQ metadata
- Kernel IRQ sources
- PCI MSI/MSI-X context where available

It turns traditionally dense interrupt tables into a structured inspector without changing the underlying meaning.

---

### SELinux Inspector

A dedicated graphical inspector for SELinux state and policy-facing information.

- Status and enforcement state
- Booleans
- Process contexts
- Recent AVC denials
- File Context Check
- Narrow, explicit privileged inspection where ordinary access is insufficient

Privilege is never treated as permission to run the whole application as root.

---

### Journal Inspector

A focused graphical face for the systemd journal.

- Boot selection
- Time-period filtering
- Priority thresholds
- Search and metadata
- Explicit scanning
- Read-only inspection and export

Journal Inspector stays separate from the Kernel Ring Buffer and other event sources so that each tool remains clear about where its data comes from.

---

### Boot Timing

A specialist view of where boot time went.

- Unit activation timing
- Boot phases and milestones
- Critical-path analysis
- Per-unit timing details
- Optional `/var/log/boot.log` supporting evidence

Boot Timing deliberately remains about **timing**, rather than becoming a generic boot-troubleshooting application.

---

## More LinSpectacles applets

The wider project includes inspectors for areas such as:

**Kernel Modules · Kernel Ring Buffer · Kernel Pressure · Kernel Tunables · Crypto Registry · Mounted Filesystems · Block Devices · Initramfs · Installed Software · Python Packages · Coredumps · File Handles · Environment Variables · D-Bus · IPC · Namespaces · Resolver · Timekeeping · Login state · Path inspection · Boot loaders · Autostart discovery · IPC and Namespace inspection**

Some are mature daily-use tools; others are experimental applets used to explore a subsystem before their interfaces are frozen.

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

## LinSpectacles Suite

The **LinSpectacles Suite** is the optional host/workbench for the applet family.

The applets remain independently useful. The Suite adds shared navigation and optional modules without turning standalone inspectors into tightly coupled components.

Suite modules include capabilities such as:

- **Applet Organizer**
- **Boot Environment**
- **Encyclopedia & What’s This?**
- **Privileged Helpers**
- **System Identity**
- **System Pulse**

The architectural rule is simple:

> **Inspectors inspect Linux. Suite modules enhance the workbench.**

---

## Project direction

LinSpectacles is gradually building a broad Linux inspection toolkit while keeping subsystem boundaries explicit.

Current and future work explores areas such as:

- deeper filesystem and block-device inspection
- process and kernel event tracing
- access and permission analysis
- file verification and integrity evidence
- richer cross-inspector relationships inside the Suite

The goal is not to reproduce another platform’s utility collection one-for-one.

The goal is to build the inspection toolkit that **Linux itself naturally suggests**.

---

## Repositories

Browse the organisation for individual applets, Suite components, experiments and source releases:

**https://github.com/linspectacles/**

Each repository documents its own current status, dependencies, version and usage.

---

## Philosophy in one line

**Expose the subsystem. Preserve the evidence. Keep the tool focused.**
