# NewOS_Manifesto
If I were to spin my own Distro, what would I do?

Why?
I've loved Linux ever since purchasing my first SUSe Linux box back in the late-90's.  Linux has always excited me but over the years, it's been hard to settle on a distribution.  There are great pieces and philosophies around the community but nothing that combines them all.  Perhaps there is a way to combine them all...

1.  Core Philosophy

Create a best-of-breed, modular, lean workstation operating system that takes full advantage of the underlying hardware.  The system should have broad compatibility while shedding legacy code bloat and support binary and from-source packaging available on a per-package basis.

2.  Architecture

Boot & Core Runtime
- Bootloader (Limine): Minimalist bootloader supporting EFI.  Works well with BTRFS snapshot rollbacks and is user customizable.
- File System (BTRFS + Snapper): BTRFS brings native compression and file system flexibility.  Snapper allows for an atomic-like system rollbacks without the complexity of immutable distributions.
- Init & Process Management (systemd): While a controversial choice, systemd maximizes system compatibility for snapper rollbacks as well as applications.

 Compiler & C Standard Library
 - Compiler (LLVM/Clang/LLD): Leveraging an optimized compiler will gain more secure builds and smaller binaries.
 - C Standard Library (musl libc + gcompat):  Clean and highly modular musl libc to replace glibc.  gcompat utilized to maintain compatibility where needed.

Userland
- Core Utilities with a twist (uutils/coreutils):  non-GNU binary compatible core utilities written in Rust.  The intent is to squeeze out more optimization and security without sacrificing compatibility by moving to busybox or other options.

3. Package Management (still under consideration)

The closest model would be Gentoo's emerge which allows for source-based and binary package installation.  I'd like to take this a step further though.

- Binary by Default: musl compiled packages for a fast, uniform initial installation and available simplicity.
- Persistent Source Overrides: The ability to install one, some or all of your packages from source.  The package manager maintains a 
