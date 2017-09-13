BIN_DIR=../bin

GCC=g++
MALLOC=/usr/include/malloc
INCLUDEDIR=-I$(MALLOC)
LIBDIR=-lm -pthread
CPPFLAGS = -O3 -Wall -march=native -funroll-loops -Wno-unused-result -Wno-int-to-pointer-cast
TARGET = train predict
OBJS_TRAIN = train.o Doc2Vec.o TrainModelThread.o Vocab.o NN.o TaggedBrownCorpus.o WMD.o
OBJS_PREDICT = predict.o Doc2Vec.o TrainModelThread.o Vocab.o NN.o TaggedBrownCorpus.o WMD.o

all: ${TARGET}
	mv  ${TARGET} ${BIN_DIR}

clean:
	rm -f *.o $(TARGET)
	rm -f ${BIN_DIR}/*

train : $(OBJS_TRAIN)
	$(GCC) $(CPPFLAGS) $^ $(LIBDIR) -o $@

predict : $(OBJS_PREDICT)
	$(GCC) $(CPPFLAGS) $^ $(LIBDIR) -o $@

%.o	: %.cpp
	$(GCC) $(CPPFLAGS) -c $< -o $@ $(INCLUDEDIR)
