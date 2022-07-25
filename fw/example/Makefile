EXAMPLES = hello fibonacci fibonacci-big counter

TARGET = $(addsuffix .bin, ${EXAMPLES})

.PHONY: clean
.PRECIOUS: %.hex

%.bin: %.hex
	@objcopy -Iihex "$<" -Obinary "$@"

%.hex: %.crasm
	crasm "$<" -o "$@" >> build.log

all: ${TARGET}

clean:
	@rm -f *.hex *.bin *.log
