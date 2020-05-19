#
# Make the x11 client library
#
EBIN = ../ebin

OBJS = \
	$(EBIN)/gx.beam \
	$(EBIN)/xproto.beam \
	$(EBIN)/xauth.beam \
	$(EBIN)/xcli.beam \
	$(EBIN)/xregion.beam \
	$(EBIN)/x.beam \
	$(EBIN)/x_demo.beam \
	$(EBIN)/x_run.beam

ERLC = erlc
ERL  = erl
ERLC_FLAGS = -DENDIAN=big -I../include

all: $(OBJS)

clean:
	rm $(OBJS) xproto.gx.hrl xproto.gx.erl

xproto.gx.hrl:	xproto.h
	$(ERL) -noshell -pa ../ebin -s gx start xproto.h

$(EBIN)/%.beam:	%.erl
	$(ERLC) -o $(EBIN) $(ERLC_FLAGS) -MMD -M -MF depends/$<.dep $<

-include $(OBJS:%.beam=depends/%.erl.dep)
