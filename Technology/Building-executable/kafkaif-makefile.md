
I used the following Makefile to build a test Kafka producer and consumer  
```make

bin:=bin
src:=src
inc := $(src)
inc_flags := -I$(inc)
exe_sender := $(bin)/testSender.out 
exe_receiver := $(bin)/testReceiver.out 
objs_sensder := testSender.o ProducerFacade.o KafkaIf.o
objs_sensder := $(objs_sensder:%=$(bin)/%)
objs_receiver := testReceiver.o ConsumerFacade.o KafkaIf.o
objs_receiver := $(objs_receiver:%=$(bin)/%)
executables := $(exe_sender) $(exe_receiver)
sources := $(wildcard $(src)/*.cpp)
#objects := main.o KafkaIf.o ProducerFacade.o ConsumerFacade.o
#objects := $(objects:%=$(bin)/%)
objects := $(sources:$(src)%.cpp=$(bin)%.o)
deps := $(objects:.o=.d)
CXXFLAGS := -Wall -Wextra -pedantic -Wunused -std=c++11
CPPFLAGS := $(inc_flags) -MMD -MP
LDLIBS := -lrdkafka++

all: $(executables)

testBuild :
	@ echo "sources:$(sources)"
	@echo objects:$(objects)
	@echo deps:$(deps)
	@echo T_$(VPATH)_T
	@echo $(shell find $(src) -name *.cpp)
	@echo CXXFLAGS:$(CXXFLAGS),CPPFLAGS:$(CPPFLAGS),LDLIBS:$(LDLIBS)

# linking sender
$(exe_sender) : $(objs_sensder)
	$(CXX) $(objs_sensder) $(LDFLAGS) $(LDLIBS) -o $@

# linking receiver
$(exe_receiver) : $(objs_receiver)
	$(CXX) $(objs_receiver) $(LDFLAGS) $(LDLIBS) -o $@

# $(executables) : $(objects)
#	$(CXX) $(objects) $(LDFLAGS) $(LDLIBS) -o $@

# compiling with pattern rule
bin/%.o : src/%.cpp
	mkdir -p $(@D)
	$(CXX) $(CXXFLAGS) $(CPPFLAGS) -c $< -o $@


.PHONY: clean
clean:
	rm -r $(bin)

-include $(deps)
```

shell command to find all sources:  
```make
# Find all the C and C++ files we want to compile
# Note the single quotes around the * expressions. Make will incorrectly expand these otherwise.
SRCS := $(shell find $(SRC_DIRS) -name '*.cpp' -or -name '*.c' -or -name '*.s')
```

Helpful Links:  
https://makefiletutorial.com/#makefile-cookbook  
https://docs.oracle.com/cd/E19504-01/802-5880/6i9k05dhg/index.html  
https://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/
