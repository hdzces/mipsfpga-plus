
# MIPSfpga-plus makefile
# Stanislav Zhelnio, 2019

help:
	$(info make help   - show this message)
	$(info make all    - clean, create the board project and run the synthesis)
	$(info make clean  - delete synth folder)
	$(info make create - create the board project)
	$(info make open   - open the board project)
	$(info make build  - build the board project)
	$(info make load   - program the FPGA board)
	@true

CABLE_NAME   ?= "USB-Blaster"
BUILD_DIR    ?= project
PROJECT_NAME ?= $(notdir $(CURDIR))

all: create build

clean:
	rm -rf $(BUILD_DIR)

create:
	rm -rf $(BUILD_DIR)
	mkdir  $(BUILD_DIR)
	cp *.qpf $(BUILD_DIR)
	cp *.qsf $(BUILD_DIR)
	cp *.sdc $(BUILD_DIR)

open:
	cd $(BUILD_DIR) && quartus $(PROJECT_NAME).qpf &

build:
	cd $(BUILD_DIR) && quartus_sh --flow compile $(PROJECT_NAME)

load:
	cd $(BUILD_DIR) && quartus_pgm -c $(CABLE_NAME) -m JTAG -o "p;$(PROJECT_NAME).sof"
