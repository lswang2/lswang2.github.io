# Chisel3 cookbook


## module & port
making new module in Chisel3
~~~~
module  my_module(
  input clock,
  input reset,
  
  input [7:0] inA,
  output outB
);
...

endmodule
~~~~~

~~~~~
class my_module extends Module{
  val io = IO(      // making IO ports
    new Bundle{     // Port bundle: childs--> Input/Output/Analog/Bundle
      // clock, reset are connected automatically
      val inA = Input(UInt(8.W))  // 8 bit unsigned int input
      val outB = Output(UInt(1.W))  // 1 bit output
    }
  )
  .....
}
~~~~~

Making wrapper for Chisel3 to use existing verilog design.
~~~~~
class my_module extends BlackBox{
  val io = IO(    // BlackBox will remove io in the port name
    new Bundle{
    }
  )
}
~~~~~







## signal

register
~~~~
val regname = Reg(UInt(1.W)) // 1bit register
val regname = Reg(UInt(8.W)) // 8bit register
val regname = Reg(Bool())    // boolean(=~ 1bit) register
val regname = RegInit(0.U(8.W)) // 8bit register with reset

regname := othersignal   // latch othersignal data into regname F/F
when(enable){
  regname : othersignal   // latch othersignal data into regname F/F if enable is true
}
~~~~

wire
~~~~
val wirename = Wire(UInt(1.W)) // 1bit wire
val wirename = Wire(UInt(8.W)) // 8bit wire

wirename := othersignal   // assign othersignal into wirename net

val wirename = othersignal  // define wirename implicitly and assign othersignal into it
~~~~




## statements
when statements
~~~~
when(condition0){
  statement when condition 0
}.elsewhen(condition1){
  statement when condition 1
}.elsewhen(condition2){
  statement when condition 2
}.othersize{
  statement deffault
}
~~~~




## vec/seq
data
~~~~
val vecname = Reg(Vec(size, UInt(8.W))) // 8bit x size data register
val seqname = for(i <- 0 until 8) yield { Reg(UInt(32.W) } // 32bit x 8 register generation
~~~~
operations
~~~~
val reduced = vecname.reduce(_|_)
val wirename = vecname.asUInt
~~~~

## Bundle
~~~~
class MyBundle extends Bundle{
  val a = UInt(1.W)
  val b = UInt(3.W)
  val c = Uint(4.W)
}
....
// pack
val bun = Wire(new MyBundle)
...
val uint = bun.asUInt

// unpack
val bun_new = uint.asTypeOf(new MyBundle)
... := bun_new.a
... := bun_new.b
... := bun_new.c
~~~~



## for/foreach/map

~~~~~
// for loop
for(variable <- iterable)[yield]{
  // statements
}

// foreach loop
iterable foreach { case(i) => {
    // statements using i
  }
}

(iterable zip iterable2) foreach { case(a,b) => {
    // statement usign a,b
  }
}

(iterable zipWithIndex) foreach { case(a,i) => {
    // statements using variable with index
  }
}

iterable map (statements) // Array result
iterable map (_.subvariable)
iterable map ( variable => variable.subvariable )
// is the same with
iterable foreach yield {
  case(variable) => {
    statements...
    variable.subvariable
  }
}
// is the same with
for(variable <- iterable) yield {
  statements...
  variable.subvariable
}
~~~~~



