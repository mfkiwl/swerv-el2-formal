# swerv-el2-formal
Adding RISC-V Formal Interface to Swerv-el2 processor
# Work done:
1. Added RVFI ports
2. Added RVFI signals
3. Added correct clock and reset signal
4. Added correct enable signal for rvfi_rs1_addr_d, rvfi_rs2_addr_d, rvfi_rs1_data_d, rvfi_rs2_data_d
5. Added correct rs1, rs2 and rs3 data
6. Added 2 output RVFI ports to el2_dec using `ifdef
7. Added 2 RVFI signals in el2_swerv and connected them implicitly using .name
8. Added correct rs1, rs2 and rs3 address
