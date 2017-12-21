SHELL=/bin/sh
BENCHMARK=dt
BENCHMARKU=DT

include ../config/make.def

include ../sys/make.common
#Override PROGRAM
DTPROGRAM  = $(BINDIR)/$(BENCHMARK).$(CLASS).x

OBJS = dt.o DGraph.o rapl_read.o\
	${COMMON}/c_print_results.o ${COMMON}/c_timers.o ${COMMON}/c_randdp.o


${PROGRAM}: config ${OBJS}
	${CLINK} ${CLINKFLAGS} -o ${DTPROGRAM} ${OBJS} ${CMPI_LIB} -lm

.c.o:
	${CCOMPILE} $<

rapl_read.o:         rapl_read.c
dt.o:             dt.c  npbparams.h rapl_read.h
DGraph.o:	DGraph.c DGraph.h

clean:
	- rm -f *.o *~ mputil*
	- rm -f dt npbparams.h core
