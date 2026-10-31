# SigmaOS System Info

Rust data models for USB, GPU, PCI, BIOS/UEFI, and system summary information.
`SystemInfoManager` accepts records through its `add_*` and `set_*` methods and
provides lookup and grouping operations.

## Collection and privacy limits

The manager does not probe sysfs, query firmware, enumerate PCI devices, or
collect system facts itself. Reported values are only as authoritative as the
caller-provided records; default fields can be empty or false. Do not present a
default value as a detected hardware fact.

Diagnostics should be read-only by default and redact secrets or sensitive
identifiers. A future collector should document supported platforms, data
sources, permissions, and evidence for each reported field.

## Development

The crate depends on `SigmaOS-kernel` through a sibling path dependency. CI
resolves SigmaOS path dependencies and runs `cargo test --all-targets --locked`.
