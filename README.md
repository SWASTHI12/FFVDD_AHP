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

![screenshot of code coverage]
(https://photos.app.goo.gl/6BfbmSiWar6qwqeDA)

![screenshot of waveform]
(https://photos.app.goo.gl/Gityb9uj1fdkwnVp8)

![pdf of the project]
(https://www.canva.com/design/DAFyGVbt3MU/Fg1V4eEKzMK3Bc-ON-xC1A/edit?utm_content=DAFyGVbt3MU&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

