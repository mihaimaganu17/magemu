# Components
1. PE Parser -> We need to parse the Portable Executable file format so we know
how to load it in memory:
    a Considerations:
        - We need to handle the following cases:
            - PE32
            - PE32+ (which is x64 bits)
            - ARM vs x86(most used archs)
            - DLL vs EXE files
2. SesionManager -> Manages the current opened sessions
3. Session -> An active "computer"/"station" with a desktop and at least 1 window
4. Profiler -> Generates an execution report for all runs that occur within a
binary emulation
    - Has a Run object that logs everything that happens for one of the
      following objects:
        - a process
        - a thread,
        - a callback,
        - an exported function
        - a child process
5. Register state -> State where we know the value of each register
6. Memory Manager -> Manages the memory mappings
7. Memory Mapping -> A mapping of a certain kind of memory: heap/pool alloc,
    binary image)
8. Hooks -> Callbacks for every action that an executable does
    a. Considerations:
        - Function for a specific event type or address
        - Need the following abilities:
            - Add
            - Remove
            - Enable,
            - Disable
    b. Hook types:
        - Code hooks
        - Memory access hooks
        - memory invalid hook
        - memory permission execute hook
        - memory permission write hook
        - memory read
        - memory write
        - hook interrupt
        - hook instruction
        - api hooks
        - dynamic code hooks

9. Emulation engine -> Need a cpu emulation engine(Unicorn engine)
10. RegistryManager -> Manages registry keys
11. FileManager -> Manages file system activity during emulation
    Manages:
        - FileMap -> Object representing a memory mapped file
        - File -> Object representing a file/directory
12. DecoyModule -> Class that represents "decoy" modules that are loaded into
    emulated memory. We use decoy modules so that shellcode (or other modules)
    can parse the PE file to resolve exports
13. JitPeFile -> Class used to rapidly assemble a decoy PE that will only
    contain an export table so malware can parse it.
14. Network Manager -> Manages network connections during emulation
    Considerations:
        - sockets
        - wininets
        - curr_fd, curr_handle
        - dns
15. DriveManager -> Manages the emulation of Windows drives
16. CryptoManager -> Manages the emulation of crypto function
17. Windows Api
18. Process envinronment block
