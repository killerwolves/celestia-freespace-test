DISC2MAP_OBJS   = disc2map.o
DISC2MAP_LIBS   = -lm -lnetpbm

POF2CMOD_OBJS   = pof2cmod.o cmod.o pof.o bsp.o
POF2CMOD_LIBS   = -lm

GALAXY_OBJS     = galaxy.o
GALAXY_LIBS     = -lm

PROGRAMS        = pof2cmod disc2map galaxy eqt2gal gal2ecl

.PHONY : all clean depend

all: depend $(PROGRAMS)

pof2cmod: $(POF2CMOD_OBJS)
	$(CC) -o $@ $+ $(POF2CMOD_LIBS)

disc2map: $(DISC2MAP_OBJS)
	$(CC) -o $@ $+ $(DISC2MAP_LIBS)

galaxy: $(GALAXY_OBJS)
	$(CC) -o $@ $+ $(GALAXY_LIBS)

eqt2gal: galaxy
	cp $+ $@

gal2ecl: galaxy
	cp $+ $@

%.d: %.c
	@set -e; rm -f $@; \
	  $(CC) -MM $(CFLAGS) $< > $@.$$$$; \
	  sed 's,\($*\)\.o[ :]*,\1.o $@ : ,g' < $@.$$$$ > $@; \
	  rm -f $@.$$$$

clean:
	rm -f *.o *.d *.d.* $(PROGRAMS)

depend: $(OBJS:.o=.d)

sinclude $(OBJS:.o=.d)
