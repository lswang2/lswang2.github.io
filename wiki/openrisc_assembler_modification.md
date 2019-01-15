OpenRISC Assembler Modification
===============================

# cgen

[cgen]:https://sourceware.org/cgen/ is needed to generate assembler code for or1k.
download [latest]:ftp://sourceware.org/pub/cgen/snapshots/latest.tar.bz2 snapshot and make some bug fix to use it.

* opcodes_error_handler macro definition should be generated to or1k-desc.h file instead of or1k-desc.c file


# modification points

## instruction definition

    (dni
      ld-add ; instruction name
      "ld-add reg/reg/reg" ; comment
      ((MACH ORBIS-MACHS)) ; attrs
      "ld.mul $rD,$rA,$rB" ; syntax
      (+			; add belows : format
        OPC_DSP		; opcode enum value. it contains bit field and value
        rD			; hardware register. it contains bit field and value
        rA			; hardware register. it contains bit field and value
        rB			; hardware register. it contains bit field and value
        (f-resv-10-3 0)	; reserved bit field filled with 0
        OPC_DSP_ADD	; sub opcode enum value
      )
      (set SI rD (add rA rB))	; semactics, maybe not used in assembling
      ()	; timing
    )

## emums definition

## macro definition

# cgen build flow
- download binutils from https://github.com/openrisc/binutils_gdb
- download cgen from ftp://sourceware.org/pub/cgen/snapshots/
- uncompress cgen
- edit binutils_gdb/cpu/or1korbis.cpu for new instructions

~~~~
copy -r ./cgen-date/cgen ./binutils_gdb/
mkdir build
cd build

../binutils_gdb/configure
make -j4

cd opcodes

make stamp-or1k

cd ../../binutils-gdb/opcodes
ls or1k-*
~~~~


# new instructions

# compare instructions





