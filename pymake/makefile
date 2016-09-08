PROGRAM = ../bin/helloworld.mac

BINDIR=../bin/
SOURCEDIR1=../src/

OBJDIR = ./obj_temp

VPATH = \
${SOURCEDIR1} 

.SUFFIXES: .c .cpp .f .f90 .F90 .fpp .o

# Define the Fortran compile flags
F90 = gfortran
F90FLAGS = -O2 -fbacktrace -ffpe-summary=overflow 

# Define the C compile flags
CC = gcc
CFLAGS = -O3 -D_UF 

# Define the libraries
SYSLIBS = -lc 

OBJECTS = \
$(OBJDIR)/helloworld.o 

# Define task functions

all: makebin | helloworld

makebin:
	mkdir -p $(BINDIR)

# Define the objects that make up helloworld.mac
helloworld: $(OBJECTS)
	-$(F90) $(F90FLAGS) -o $(PROGRAM) $(OBJECTS) $(SYSLIBS) -I$(OBJDIR) -J$(OBJDIR) 

$(OBJDIR)/%.o : %.f
	@mkdir -p $(@D)
	$(F90) $(F90FLAGS) -c $< -o $@ -I$(OBJDIR) -J$(OBJDIR) 

$(OBJDIR)/%.o : %.f90
	@mkdir -p $(@D)
	$(F90) $(F90FLAGS) -c $< -o $@ -I$(OBJDIR) -J$(OBJDIR) 

$(OBJDIR)/%.o : %.F90
	@mkdir -p $(@D)
	$(F90) $(F90FLAGS) -c $< -o $@ -I$(OBJDIR) -J$(OBJDIR) 

$(OBJDIR)/%.o : %.fpp
	@mkdir -p $(@D)
	$(F90) $(F90FLAGS) -c $< -o $@ -I$(OBJDIR) -J$(OBJDIR) 

$(OBJDIR)/%.o : %.c
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -c $< -o $@


$(OBJDIR)/%.o : %.cpp
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -c $< -o $@


.PHONY : clean
clean : 
	-rm -rf $(OBJDIR)

.PHONY : cleanall
cleanall : 
	-rm -rf $(OBJDIR) $(BINDIR)

