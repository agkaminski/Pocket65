all: main.crasm
	@crasm main.crasm -o fw.hex > build.log
	@grep "Code length" build.log

clean:
	rm -f fw.hex build.log
