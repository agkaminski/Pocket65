GOAL = fw

TARGET = $(addsuffix .bin, ${GOAL})
LOG = $(addsuffix .log, ${GOAL})

.PHONY: clean
.PRECIOUS: %.hex

%.bin: %.hex
	@objcopy -Iihex "$<" -Obinary "$@"

%.hex: %.crasm
	@crasm "$<" -o "$@" > ${LOG}

all: ${TARGET}

clean:
	@rm -f *.hex *.bin *.log
