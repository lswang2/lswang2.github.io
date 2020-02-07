OpenRISC BSP
===============================

# Newlib에 새로운 board를 추가하기

## 파일 수정

libgloss/or1k/boards/ 에 기존 파일을 복사하여 새로운 파일을 생성 후 필요한 부분을 수정한다.

**ml501.S**
~~~~
#include "../include/or1k-asm.h"
#include "../include/or1k-nop.h"

/*
 * Define symbols to be used during startup - file is linked at compile time
 *
 */
.weak _or1k_board_mem_base
.weak _or1k_board_mem_size
.weak _or1k_board_clk_freq

_or1k_board_mem_base:   .long   0x0
_or1k_board_mem_size:   .long   0x800000

_or1k_board_clk_freq:   .long   66666666

/* Peripheral information - Set base to 0 if not present*/
.weak _or1k_board_uart_base
.weak _or1k_board_uart_baud
.weak _or1k_board_uart_IRQ

_or1k_board_uart_base:  .long   0x90000000
_or1k_board_uart_baud:  .long   115200
_or1k_board_uart_IRQ:   .long   2

.weak _or1k_board_exit
_or1k_board_exit:
    l.nop OR1K_NOP_K_EXIT_QUIET
.Lexitloop:
    OR1K_DELAYED_NOP(l.j .Lexitloop)

.global _or1k_board_init_early
_or1k_board_init_early:
    OR1K_DELAYED_NOP(l.jr r9)

.weak _or1k_board_init
_or1k_board_init:
    OR1K_DELAYED_NOP(l.jr r9)
~~~~
.weak로 되어 있는 변수는 추후 app compile과정에서 개별적으로 수정하여 반영할 수 있으므로
현재로서는 잘못되어 있어도 큰 문제는 없다.

libgloss/or1k/Makefile.in의 BOARDS에 새로운 파일을 추가한다. 

## Compile Newlib and Install

~~~~
make
make install
~~~~

# Board에 맞게 컴파일 하기

## gcc
아래와 같이 컴파일하면 해당 board의 설정이 자동으로 로드된다.
~~~~
or1k-elf-gcc source.c -o target.elf -mboard=NEWBOARD
~~~~

## BSP의 변수 app에서 수정하기
app source에서 아래와 같이 전역변수로 BSP의 변수를 새로 지정하면 완전히 override할 수 있다.
~~~~
// board rate를 57600으로 변경 
unsigned long _or1k_board_uart_baud = 57600;
~~~~

