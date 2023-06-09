Download Link: https://assignmentchef.com/product/solved-ee2003-assignment1-sequential-multiplier-in-verilog-hdl
<br>



This assignment deals with implementation of a sequential multiplier in Verilog HDL.

## Goals

– Demonstrate basic working knowledge of verilog– Practice git– Practice assignment submission and feedback

## Given

– Test bench for sequential multiplier– Template code that you can use to fill in– Some test cases

## Details on the assignment

### Multiplication

This basically refers to the “long form” multiplication as we learn in school. For each digit of the multiplier, we shift the multiplicand to the appropriate place value, and then add all the partial products. An example of the partial products in binary for a simple 4-bit multiplication are shown below. As expected, multiplying two 4-bit numbers can result in an output that is up to 8 bits in length.

“`0110 # Decimal 6 – Multiplicandx 0011 # Decimal 3 – Multiplier——–0110 # Partial product 0 (PP0)0110 # PP10000 # PP20000 # PP3——–00010010 # Decimal 18——–“`

### Number representation

The numbers themselves are represented in 2’s complement notation. Therefore, if the multiplicand is negative, the PP values should be “sign-extended” to get the correct result. An example for negative multiplicand is shown below – negative multiplier requires similar careful handling, and is left as an exercise.

“`1010 # Decimal -6x 0011 # Decimal 3——–11111010 # Partial product 0 (PP0) – sign extended1111010 # PP1000000 # PP200000 # PP3——–(1)11101110 # Decimal -18 (discard the overflow 1)——–“`

### Hardware implementation

The above multiplication process can be directly implemented as combinational logic, where each partial product vector is created using a set of AND gates, and the results are put through a chain of adders.

The other alternative is to have a reduced hardware with a single register to hold the final product. This **accumulates** the final product by iterating over several clock cycles (how many?). A diagram indicating the architecture is shown here.

![Sequential Multiplier](./fig/seqmult.png)

## HowTo

Fork this repostiry (`EE2003/a1`) into your namespace so that you can edit and push changes.

You are given a test bench (`seq_mult.v`) with suitable test cases (`test_in.dat`). The assignment repository also contains a `drone` configuration that will run the tests using the `iverilog` compiler. You can of course run the test commands yourself if you wish, as seen in the configuration file.

**IMPORTANT**: the filename for the code that you write must be `seq_mult.v` – otherwise the auto-grader will not recognize it.

Once you have confirmed that your code passes all the tests, commit all the changes, tag it for submission, and push to your repository.