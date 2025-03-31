# 152final


https://drive.google.com/drive/folders/1Dus4d-FdjdItmU_WTIFt2IpsDFlMQF2b


`timescale 1ns / 1ps

module four_bit_counter_tb;

reg clk, reset, enable;
wire [3:0] count;

// Instantiate the counter
four_bit_counter uut (
    .clk(clk),
    .reset(reset),
    .enable(enable),
    .count(count)
);

// Generate clock (toggle every 5ns)
always #5 clk = ~clk;

initial begin
    clk = 0; reset = 1; enable = 0;  // Initialize
    #10 reset = 0; enable = 1;       // Start counting
    #50 enable = 0;                  // Pause
    #20 reset = 1;                   // Reset again
    #10 $stop;                        // End simulation
end

endmodule
