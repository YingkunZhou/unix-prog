.PHONY: all clean

subdir = c1 c2 c3 c4 c5 c6 c7 c8 c9 # common

RESULT = $(addprefix .stamps/, $(subdir))

all: $(RESULT)

$(RESULT): .stamps/% : %
	mkdir -p $</build
	$(MAKE) -C $< AUPSRC=$(PWD) \
		OS=LINUX \
		LIBS=-lncurses \
		LIBS+=-lutil \
		LIBS+=-lrt \
		LIBS+=-lpthread \
		TLIBS=-pthread
	mkdir -p $(dir $@) && touch $@

clean:
	rm -rf .stamps
	for d in $(subdir) ; do \
		$(MAKE) -C $$d clean ; \
	done
