#------------------------------------------------------------------------------
# Makefile for sample HDF code
#------------------------------------------------------------------------------

# Set up compile options
CC = gcc
RM = rm -f
EXTRA = -Wall -g

# Define the include files
INC = bool.h const.h date.h error_handler.h input.h myhdf.h mystring.h \
output.h space.h si.h
INCDIR  = -I. -I$(HDFINC) -I$(HDFEOS_INC) -I$(HDFEOS_GCTPINC) -I$(JPEGINC) -I$(SZIPINC) -I$(ZLIBINC)
NCFLAGS = $(EXTRA) $(INCDIR)

# Define the source code and object files
SRC = date.c              \
      error_handler.c     \
      get_args.c          \
      input.c             \
      make_spectral_index.c \
      myhdf.c             \
      mystring.c          \
      output.c            \
      space.c             \
      spectral_indices.c
OBJ = $(SRC:.c=.o)

# Define the object libraries
LIB   = -L$(HDFLIB) -lmfhdf -ldf -lxdr -L$(JPEGLIB) -ljpeg \
        -L$(ZLIBLIB) -lz -L$(SZIPLIB) -lsz -lm
##LIB   = -L$(HDFLIB) -lmfhdf -ldf -lxdr -L$(JPEGLIB) -ljpeg \
##        -L$(ZLIBLIB) -lz -L$(SZIPLIB)/libsz.a -lm
EOSLIB = -L$(HDFEOS_LIB) -lhdfeos -L$(HDFEOS_GCTPLIB) -lGctp

# Define the executable
EXE = spectral_indices

# Target for the executable
all: $(EXE)

spectral_indices: $(OBJ) $(INC)
	$(CC) $(EXTRA) -o $(EXE) $(OBJ) $(EOSLIB) $(LIB)

install:
	cp $(EXE) $(BIN)

clean:
	$(RM) *.o $(EXE)

$(OBJ): $(INC)

.c.o:
	$(CC) $(NCFLAGS) -c $<
