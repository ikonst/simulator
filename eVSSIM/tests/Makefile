OBJ = system_tests.o object_tests.o sector_tests.o

VSSIM_OBJ = vssim_config_manager.o \
			ftl.o ftl_mapping_manager.o ftl_inverse_mapping_manager.o \
			ftl_gc_manager.o ftl_perf_manager.o \
			ssd.o ssd_log_manager.o ssd_io_manager.o \
			ftl_sect_strategy.o ftl_obj_strategy.o

#CFLAGS = -I/opt/gtest/include -I../osc-osd -I../osc-osd/osd-target -g -DGTEST -DFTL_DEBUG -DNO_OSD
CFLAGS = -I/opt/gtest/include -I../osc-osd -I../osc-osd/osd-target -g -DGTEST -L/opt/gtest/lib

all: sector_tests object_tests

sector_tests: sector_tests.o $(VSSIM_OBJ)
	g++ $(CFLAGS) -Wall -o sector_tests sector_tests.o $(VSSIM_OBJ) -lpthread -lgtest -lgtest_main

object_tests: object_tests.o $(VSSIM_OBJ)
	g++ $(CFLAGS) -Wall -o object_tests object_tests.o $(VSSIM_OBJ) -Wl,-Bstatic -L../osc-osd/osd-util -L../osc-osd/osd-target -losdutil -losdtgt -Wl,-Bdynamic -lsqlite3 -lm -lpthread -lgtest -lgtest_main

%.o: %.cc
	g++ -Wall $(CFLAGS) -c $<

%.o: %.c
	gcc -Wall $(CFLAGS) -c $<

.PHONY: clean distclean mklink

clean:
	rm -f object_tests sector_tests object_tests.o sector_tests.o $(VSSIM_OBJ) data/*

distclean: clean
	rm -f ssd.{h,c} ssd_io_manager.{h,c} ssd_log_manager.{h,c} ssd_util.h common.h \
		ftl.{h,c} ftl_sect_strategy.{h,c} ftl_obj_strategy.{h,c} ftl_type.h ftl_gc_manager.{h,c} ftl_inverse_mapping_manager.{h,c} \
		ftl_mapping_manager.{h,c} ftl_perf_manager.{h,c} vssim_config_manager.{h,c} \
		ssd_monitor uthash.h

mklink:
	ln -s ../SSD_MODULE/ssd.h
	ln -s ../SSD_MODULE/ssd.c
	ln -s ../SSD_MODULE/ssd_io_manager.h
	ln -s ../SSD_MODULE/ssd_io_manager.c
	ln -s ../SSD_MODULE/ssd_log_manager.h
	ln -s ../SSD_MODULE/ssd_log_manager.c
	ln -s ../SSD_MODULE/ssd_util.h
	ln -s ../FTL_SOURCE/COMMON/common.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl.c
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_sect_strategy.c
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_sect_strategy.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_obj_strategy.c
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_obj_strategy.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_type.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_gc_manager.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_gc_manager.c
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_inverse_mapping_manager.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_inverse_mapping_manager.c
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_mapping_manager.h
	ln -s ../FTL_SOURCE/PAGE_MAP/ftl_mapping_manager.c
	ln -s ../FTL_SOURCE/PAGE_MAP/TOOLS/uthash.h
	ln -s ../FTL_SOURCE/PERF_MODULE/ftl_perf_manager.h
	ln -s ../FTL_SOURCE/PERF_MODULE/ftl_perf_manager.c
	ln -s ../CONFIG/vssim_config_manager.h
	ln -s ../CONFIG/vssim_config_manager.c
	ln -s ../MONITOR/SSD_MONITOR_PM/ssd_monitor_p ssd_monitor
