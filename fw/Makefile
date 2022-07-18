all: main.crasm
	@crasm main.crasm -o fw.hex > build.log
	@grep "Code length" build.log
	@objcopy -Iihex fw.hex -Obinary fw.bin

clean:
	rm -f fw.hex build.log
