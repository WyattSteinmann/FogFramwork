**NOTE:** This Project Is Built Off Of https://github.com/davidcallanan/os-series/tree/ep2 OS Dev In ASM Is Not My Thing But i Can Do Some Things And C But I Am New To C

It's Like Cosmos But With ASM And C

**Setup:**

Build an image for our build-environment:

    docker build buildenv -t myos-buildenv

**Build:**

Enter build environment:

    Linux or MacOS: docker run --rm -it -v "$(pwd)":/root/env myos-buildenv
    Windows (CMD): docker run --rm -it -v "%cd%":/root/env myos-buildenv
    Windows (PowerShell): docker run --rm -it -v "${pwd}:/root/env" myos-buildenv
    Please use the linux command if you are using WSL, msys2 or git bash
    NOTE: If you are having trouble with an unshared drive, ensure your docker daemon has access to the drive you're development environment is in. For Docker Desktop, this is in "Settings > Shared Drives" or "Settings > Resources > File Sharing".

Build for x86 (other architectures may come in the future):

    make build-x86_64
    If you are using Qemu, please close it before running this command to prevent errors.

To leave the build environment, enter exit.
Build for x86 (other architectures may come in the future):
    make build-x86_64
    If you are using Qemu, please close it before running this command to prevent errors.

To leave the build environment, enter exit.

**Emulateing**

You can emulate your operating system using Qemu: For Windows Users: (Don't forget to add qemu to your path!)

    qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso
    Note: Close the emulator when finished, so as to not block writing to kernel.iso for future builds.

If the above command fails, try one of the following:

    Windows: qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso -L "C:\Program Files\qemu"
    Linux: qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso -L /usr/share/qemu/
    Alternatively, install a custom BIOS binary file and link it to Qemu using the -L option.

Alternatively, you should be able to load the operating system on a USB drive and boot into it when you turn on your computer. (I haven't actually tested this yet.)
Alternatively, you should be able to also use virtual box (I haven't actually tested this yet.)
Alternatively, you should be able to also use vmware (I haven't actually tested this yet.)
