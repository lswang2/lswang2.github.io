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





## statements





## vec/array/seq




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



