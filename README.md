# FFVDD_AHP
# Design code 
module up_counter (
    input wire clk,  // Clock input
    input wire rst,  // Reset input
    output wire [3:0] count  // 4-bit counter output
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
