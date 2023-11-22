      


# FFVDD_AHP
# Design code 



module up_counter (
    input wire clk,
    input wire rst,
    output wire [3:0] count
);
 
 
  reg [3:0] count_reg;  // 4-bit counter register

    always @(posedge clk or posedge rst) begin
        if (rst) begin
            count_reg <= 4'b0000;  // Reset the counter
        end else begin
            count_reg <= count_reg + 1;  // Increment the counter
        end
    end

    assign count = count_reg;  // Output is the value in the register

endmodule

# testbench 

module tb_up_counter;
    reg clk;
    reg rst;
    wire [3:0] count;

    // Instantiate the up_counter module
    up_counter uut (
        .clk(clk),
        .rst(rst),
        .count(count)
    );

    // Clock generation
    always begin
        #5 clk = ~clk;
    end

    // Initialize signals
    initial begin
        clk = 0;
        rst = 0;

        // Reset the counter
        rst = 1;
        #10 rst = 0;

        // Monitor the count
        $monitor("Time=%0t count=%h", $time, count);
    end

    // Simulate for some time
    initial begin
        #50 $finish;
    end

endmodule

![20231120_202843_0009](https://github.com/SWASTHI12/FFVDD_AHP/assets/131871466/6fae227f-74a0-4cbe-ba5f-9bde63446214)
![20231120_202843_0010](https://github.com/SWASTHI12/FFVDD_AHP/assets/131871466/a81cdb0e-9371-47bb-8fd0-5a2095170fbe)


![pdf of the project]
(https://www.canva.com/design/DAFyGVbt3MU/Fg1V4eEKzMK3Bc-ON-xC1A/edit?utm_content=DAFyGVbt3MU&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

