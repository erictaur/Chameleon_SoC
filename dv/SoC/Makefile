all: sim
.PHONY: all

test.hex: ../../sw/test.c ../../sw/crt0.S ../../sw/link.ld 
	$(MAKE) -C ../../sw/ all

test.vvp: test.hex files.list
	iverilog -o test.vvp -D TEST_FIL="../../sw/test.hex" -c files.list

test_fast.vvp: test.hex files_fast_sim.list
	iverilog -o test_fast.vvp -D TEST_FIL="../../sw/test.hex" -c files_fast_sim.list

test_gl.vvp: test.hex files_gl.list
	iverilog -o test_gl.vvp -DUSE_POWER_PINS -D TEST_FIL="../../sw/test.hex" -c files_gl.list

test_ys.vvp: test.hex files_fast_YS.list
	iverilog -o test_ys.vvp -D TEST_FIL="../../sw/test.hex" -c files_fast_YS.list
	
	
sim: test.vvp 
	./test.vvp

sim_fast: test_fast.vvp 
	./test_fast.vvp

sim_gl: test_gl.vvp
	./test_gl.vvp


sim_ys: test_ys.vvp
	./test_ys.vvp
	
clean:
	rm *.vvp *.vcd
	rm -f ../../sw/*.hex ../../sw/*.elf ../../sw/*.lst 
