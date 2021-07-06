.PHONY: all clean

subdir = c1 c2 c3 c4 c5 c6 c7 c8 c9 # common

RESULT = $(addprefix stamps/, $(subdir))
LIBS := -lncurses -lutil -lpthread -lrt

all: $(RESULT)

$(RESULT): stamps/% : %
	$(MAKE) -C $< AUPSRC=$(PWD) \
		OS=LINUX \
		LIBS=$(LIBS) \
		TLIBS=-pthread
	mkdir -p $(dir $@) && touch $@

clean:
	rm -rf stamps
	for d in $(subdir) ; do \
		$(MAKE) -C $$d clean ; \
	done
