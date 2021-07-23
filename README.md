# swerv-el2-formal
Adding RISC-V Formal Interface to Swerv-el2 processor
# Work done:
1. Added RVFI ports
2. Added RVFI signals
3. Added correct clock and reset signal
4. Added correct enable signal for rvfi_rs1_addr_d, rvfi_rs2_addr_d, rvfi_rs1_data_d, rvfi_rs2_data_d
5. Added correct rs1, rs2 and rs3 data
6. Added 2 output RVFI ports to el2_dec using `ifdef and  assigned proper values
7. Added 2 RVFI signals in el2_swerv and connected them implicitly using .name
8. Added correct rs1, rs2 and rs3 address
9. Added 3 RVFI ports to el2_dec using `ifdef: output logic [4:0]  rvfi_waddr_wb_dec,  output logic   rvfi_we_wb_dec,  output logic [31:0] rvfi_wdata_wb_dec and    assigned proper values
10. - assign rvfi_rd_addr_wb  = rvfi_waddr_wb_dec;
    - assign rvfi_rd_wdata_wb = rvfi_we_wb_dec ? rvfi_wdata_wb_dec : rf_wdata_lsu;
   - assign rvfi_rd_we_wb    = rvfi_we_wb_dec | rf_we_lsu;
   

   - map  exu_i0_result_x = result_ex_i,
   - map lsu_wdata = exu_lsu_rs2_d
11. Substituted lsu_wdata with exu_lsu_rs2_d 
   - lsu_addr_d contains the 32 bit computed address
   - map alu_adder_result_ex =  lsu_addr_d
12. Added RVFI signal rvfi_alu_adder_result to el2_lsu
13.Assigned rvfi_alu_adder_result = lsu_addr_d
14. Added rvfi_alu_adder_result signal declaration and connected it implicitly using .name
15. Substituted alu_adder_result_ex with rvfi_alu_adder_result
16. Map rf_wdata_lsu = lsu_result_m;
17. Added 1 output RVFI ports to el2_dec using `ifdef and  assigned proper values: rvfi_wdata_lsu_dec
18. Removed rvfi_we_lsu signal Assumption there is no write enable for load store unit

