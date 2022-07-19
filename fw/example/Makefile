EXAMPLES = hello

TARGET = $(addsuffix .bin, ${EXAMPLES})
LOG = $(addsuffix .log, ${EXAMPLES})

.PHONY: clean
.PRECIOUS: %.hex

%.bin: %.hex
	@objcopy -Iihex "$<" -Obinary "$@"

%.hex: %.crasm
	@crasm "$<" -o "$@" > ${LOG}

all: ${TARGET}

clean:
	@rm -f *.hex *.bin *.log
