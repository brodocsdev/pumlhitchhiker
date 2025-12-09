PUMLS := $(shell find . -name '*.puml')
PNGS  := $(PUMLS:.puml=.png)

all: $(PNGS)

%.png: %.puml
	@echo "Generating $@ from $<"
	touch $@
	

clean:
	rm -f $(PNGS)