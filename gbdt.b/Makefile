ext_obj = ../util/hash.o ../util/str.o ../regr/auc.o

objs    = gblr.o gbdt.o dtree.o tdata.o     gbm.o gbmr.o   gbrank.o
sos     = libgblr.so libgbdt.so libdtree.so libtdata.so  libgbm.so libgbmr.so libgbrank.so
statics = libgblrs.a libgbdts.a libdtrees.a libtdatas.a  libgbms.a libgbmrs.a libgbranks.a

all : $(objs) $(statics) $(sos)

lib_install :
	mkdir -p ../lib
	cp *.a ../lib
	cp *.so ../lib

inc_install :
	mkdir -p ../inc
	cp *.h ../inc

gbrank.o: gbrank.h
gbmr.o : gbmr.h
gbm.o  : gbm.h
gblr.o : gblr.h
gbdt.o : gbdt.h
dtree.o : dtree.h
tdata.o : tdata.h

libgbrank.so : gbrank.o gbdt.o dtree.o tdata.o $(ext_obj)
	$(LD) $^ -o $@

libgbmr.so : gbmr.o gbm.o dtree.o tdata.o $(ext_obj)
	$(LD) $^ -o $@

libgbm.so : gbm.o dtree.o tdata.o $(ext_obj)
	$(LD) $^ -o $@

libgblr.so : gblr.o gbdt.o dtree.o tdata.o $(ext_obj)
	$(LD) $^ -o $@

libgbdt.so : gbdt.o dtree.o tdata.o $(ext_obj)
	$(LD) $^ -o $@

libdtree.so : dtree.o tdata.o $(ext_obj) 
	$(LD) $^ -o $@

libtdata.so : tdata.o $(ext_obj)
	$(LD) $^ -o $@



libgbranks.a : gbrank.o gbdt.o dtree.o tdata.o $(ext_obj)
	ar cr $@ $^

libgbmrs.a : gbmr.o gbm.o dtree.o tdata.o $(ext_obj)
	ar cr $@ $^

libgbms.a : gbm.o dtree.o tdata.o $(ext_obj) 
	ar cr $@ $^

libgblrs.a : gblr.o gbdt.o dtree.o tdata.o $(ext_obj)
	ar cr $@ $^

libgbdts.a : gbdt.o dtree.o tdata.o $(ext_obj) 
	ar cr $@ $^

libdtrees.a : dtree.o tdata.o $(ext_obj)
	ar cr $@ $^

libtdatas.a : tdata.o  $(ext_obj)
	ar cr $@ $^


install :
	$(MAKE) lib_install
	$(MAKE) inc_install


.PHONY: clean
clean :
	rm -rf $(sos)
	rm -rf $(objs)
	rm -rf $(statics)
