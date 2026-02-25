## introduction

- **computer:** what does a computer do?
  It takes input data, processes it according to a predefined set of rules (programs), and produces output.
  Fundamentally, it is an automated data manipulator.

- **bit:** how to represent data?
  Through binary digits (0s and 1s).
  Physically, these are represented by the presence or absence of electrical voltage (high/low) within a circuit.

- **operation:** how to process data?
  By passing electronic signals through logic gates (AND, OR, NOT) built from transistors.
  These gates are arranged into complex circuits (*arithmetic logic unit*) to perform addition, subtraction, and bitwise operations.

- **memory:** how to store data?
  Using bistable circuits (like flip-flops) for incredibly fast, temporary storage inside the CPU (registers),
  or microscopic capacitors and transistors for the main system memory (RAM).
  
- **clock:** how to update the stored data?
  A quartz oscillator generates a continuous, rhythmic electrical pulse called the clock signal.
  This acts like a metronome, synchronizing the flow of data through the processor and dictating exactly when circuits should read or update their state.
  
- **operator:** how to select how to process data?
  Through an "opcode" (operation code).
  This is a specific binary pattern within an instruction that the CPU's Control Unit decodes to determine which physical circuits to activate (e.g., telling the ALU to "add" instead of "multiply").

- **operand:** how to select which data to process?
  The instruction also contains fields specifying the locations of the data.
  Operands can be addresses pointing to specific registers, memory locations in RAM, or direct numerical values embedded right in the instruction.
  
- **instruction:** how to represent operator and operand?
  As a highly structured sequence of bits known as machine code.
  A single instruction contains the opcode and the operands formatted in a specific way that the CPU architecture is hardwired to understand.
  
- **program counter:** after executed a instruction, which intruction should be executed?
  A special register called the Program Counter (PC) or Instruction Pointer.
  It holds the memory address of the next instruction.
  It automatically increments after an instruction is fetched, unless a "jump" or "branch" instruction explicitly changes its value to alter the program flow.

- **program:** how to store instructions and data?
  Under the Von Neumann architecture, both instructions and data are stored together as sequences of bytes in the same memory space (RAM).

- **mother board:** what constitutes the real computer?
  The main printed circuit board provides the physical sockets and electrical pathways that connect
  the CPU, memory, storage, and peripheral devices.
  
- **printed circuit board:** how physicaly mother board is fabricated?
  It is made of alternating layers of non-conductive fiberglass and conductive copper foil.
  The copper is chemically etched away using photosensitive masks to leave only
  the incredibly fine, precisely routed electrical traces
  
- **central processing unit:** which part of mother board executes instrucionts?
  The CPU contains the calculating unit (*Arithmetic Logic Unit*), fast but small memory (*register*),
  and control unit (*instruction decoder*).
  It is responsible for the fetch-decode-execute-writeback cycle of program instructions.
  
- **package:** what do we see when we see each parts?
  The physical casing—often black plastic, ceramic, or a metal heat-spreader.
  This casing protects the microscopic, fragile silicon chip inside and provides
  the macroscopic metallic pins or pads needed to connect it to the motherboard.

- **integrated chip:** what is inside the package?
  a silicon chip: a tiny, flat piece of semiconductor material containing
  millions or billions of microscopic electronic components intricately wired together.
  
- **semiconductor:** what constitutes integrated circuit?
  Materials, primarily silicon, whose electrical conductivity falls between that of a conductor and an insulator.
  By adding impurities and applying voltage, semiconductors can be manipulated to act as
  microscopic electronic switches.

- **gate:** how semiconductor is used for logic operation?
  By arranging the electronic switches properly, output bit can be manipulated to accept certain input bits.  
    
- **semiconductor fabrication:** how integrated circuit is fabricated?
  Through a process called photolithography.
  Light is shone through intricate masks onto photosensitive chemicals coating a silicon wafer.
  This process is repeated dozens of times to etch patterns and deposit materials layer by microscopic layer.
  
- **integrated circuit design:** how integrated circuit is designed?
  Using Hardware Description Languages.
  Digital hardware engineers write code that describes the logic and behavior of the chip,
  rather than drawing physical diagrams of transistors.
  
- **digital integrated circuit:** how much integrated circuit design for computer is automated?
  Electronic Design Automation software translates the human-written HDL code into a physical layout of logic gates,
  optimizing the electrical paths and routing the billions of microscopic wires automatically.
  
- **random access memory:** where instructions and data are stored?
  RAM acts as the computer's high-speed working workspace.
  The operating system, active programs, and the data they are currently manipulating are loaded here from
  slower, long-term storage drives.
  
- **read only memory:** where startup instructions are stored?
  In a specialized chip on the motherboard (historically ROM, now typically Flash memory like EEPROM).
  It contains the system firmware (BIOS or UEFI).
  
- **operating system:** what happens when we start the computer?
  When power flows, the CPU is hardwired to look at the firmware (BIOS/UEFI) chip for its very first instruction.
  The firmware performs a hardware check (POST), initializes the components,
  and then searches the storage drive for a bootloader.
  The bootloader loads the Operating System kernel into RAM and passes control to it,
  allowing the OS to manage the hardware and start your programs.
