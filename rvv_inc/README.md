# RVV backend include headers

`rtl/coralnpu-Subsystem.sv` `\`include`s these RVV backend config/struct headers
(from google-coral/coralnpu `hdl/verilog/rvv/inc/`, Apache-2.0). They were not
part of the original single-file vendor drop; without them the subsystem cannot
be compiled standalone.

Build with the include path + config defines:

    -I rvv_inc +define+VLEN_128 +define+TB_SUPPORT

- `VLEN_128` selects the vector length (config selector; see rvv_backend_define.svh).
- `TB_SUPPORT` enables the `uop_pc`/`last_uop_valid` trace fields that
  `RvvCoreWrapper` references (gated by `\`ifdef TB_SUPPORT` in rvv_backend_alu.svh).
