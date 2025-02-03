# Pesnik OS

A ground-up operating system implementation focused on resource management, parallelism, and performance testing. This project documents the journey of building an OS from scratch, emphasizing learning and understanding core OS concepts.

## Project Overview

Pesnik OS is an educational x86 operating system that prioritizes:
- Resource constraint management and monitoring
- Advanced threading and parallelism implementations
- Comprehensive load testing capabilities
- Minimal external dependencies
- Clean, well-documented architecture

## Technical Specifications

- **Architecture:** x86 (32-bit)
- **Bootloader:** Custom two-stage bootloader
- **Kernel Type:** Monolithic with modular design
- **Memory Management:** Paging with virtual memory support
- **Process Model:** Preemptive multitasking
- **File System:** Custom minimalist FS implementation
- **IPC:** Message passing and shared memory

## Project Structure
```
pesnik-os/
├── bootloader/
│   ├── stage1/           # First stage bootloader (512 bytes)
│   │   └── boot.asm
│   └── stage2/           # Second stage bootloader
│       ├── loader.asm
│       └── gdt.asm       # Global Descriptor Table setup
├── kernel/
│   ├── arch/             # Architecture-specific code
│   │   └── x86/
│   │       ├── boot.asm  # Kernel entry point
│   │       ├── cpu.c     # CPU initialization
│   │       └── interrupts/
│   ├── core/
│   │   ├── kmain.c       # Kernel main
│   │   ├── memory/       # Memory management
│   │   ├── process/      # Process management
│   │   ├── scheduler/    # Process scheduler
│   │   └── sync/         # Synchronization primitives
│   ├── drivers/
│   │   ├── keyboard/
│   │   ├── timer/
│   │   └── video/
│   └── lib/              # Kernel library functions
├── userspace/
│   ├── lib/              # User space libraries
│   └── programs/         # Initial userspace programs
├── tools/
│   ├── build-scripts/
│   └── testing/
└── docs/
    ├── architecture/     # Design documents
    ├── tutorials/        # Learning resources
    └── specifications/   # Implementation specs
```

## Build Requirements

### Core Tools
- NASM >= 2.15.05
- GCC >= 11.0.0
- GNU Make >= 4.3
- QEMU >= 6.2.0
- xorriso >= 1.5.4 (for ISO creation)
- GRUB2 (for bootloader development)

### Optional Tools
- GDB >= 10.0 (debugging)
- Bochs >= 2.7 (alternative emulator)
- clang-format >= 14.0 (code formatting)

## Building the OS

```bash
# Clone the repository
git clone https://github.com/pesnik/pesnik-os.git
cd pesnik-os

# Install dependencies (Ubuntu/Debian)
sudo apt-get install build-essential nasm qemu-system-x86 xorriso grub2

# Build the OS
make clean
make all

# Run in QEMU
make run
```

## Development Roadmap

### Phase 1: Bootloader and Basic Kernel (Current)
- [x] Basic bootloader implementation
- [x] Protected mode transition
- [x] Kernel loading
- [ ] Basic VGA driver
- [ ] Serial output for debugging

### Phase 2: Memory Management
- [ ] Physical memory manager
- [ ] Virtual memory (paging)
- [ ] Kernel heap allocator
- [ ] Memory mapping
- [ ] User space memory management

### Phase 3: Process Management
- [ ] Task management
- [ ] Process creation/destruction
- [ ] Context switching
- [ ] Basic scheduler
- [ ] System calls

### Phase 4: Concurrency and Parallelism
- [ ] Threading support
- [ ] Mutex implementation
- [ ] Semaphores
- [ ] Condition variables
- [ ] Multi-core support

### Phase 5: Resource Management
- [ ] Resource tracking
- [ ] Load monitoring
- [ ] Performance metrics
- [ ] Resource limits
- [ ] Load balancing

## Testing

```bash
# Run unit tests
make test

# Run integration tests
make test-integration

# Run in debug mode
make debug
```

## Debugging

GDB debugging is supported:
```bash
# Terminal 1
make debug-qemu

# Terminal 2
make debug-gdb
```

## Code Style

- C code follows the Linux kernel coding style
- Assembly follows NASM conventions
- Maximum line length: 80 characters
- Tabs: 8 spaces
- Braces: K&R style

## Documentation

- Architecture documentation in `/docs/architecture/`
- API documentation generated with Doxygen
- Learning resources in `/docs/tutorials/`
- Implementation specs in `/docs/specifications/`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to the branch
5. Create a Pull Request

## Learning Resources

### Books
- "Operating Systems: Three Easy Pieces"
- "Modern Operating Systems" by Tanenbaum
- "Operating System Concepts" by Silberschatz

### Online Resources
- OSDev Wiki (wiki.osdev.org)
- James Molloy's Kernel Development Tutorial
- Linux Kernel Documentation
- Intel Software Developer Manuals

## License

MIT License - See LICENSE file for details


## Acknowledgments

- OSDev community
