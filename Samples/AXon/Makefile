include CommonDefs.mak

BIN_DIR = Bin

# #OPENCV
# INCLUDE_DIRS = /usr/local/include/opencv2
# CXXFLAGS += -O2 -DLINUX -Wall $(INCLUDE_DIRS) `pkg-config --cflags opencv`
# LFLAGS += -lpthread -ljpeg -lrt 
# LDFLAGS = `pkg-config --libs opencv` 

#OPENCV

INC_DIRS = \
	../../Include \
	../../ThirdParty/GL/ \
	../Common

SRC_FILES = *.cpp

ifeq ("$(OSTYPE)","Darwin")
	CFLAGS += -DMACOS
	LDFLAGS += -framework OpenGL -framework GLUT
else
	CFLAGS += -DUNIX -DGLX_GLXEXT_LEGACY
	USED_LIBS += glut GL
endif

USED_LIBS += OpenNI2

EXE_NAME = AXon

CFLAGS += -Wall


ifndef OPENNI2_INCLUDE
    $(error OPENNI2_INCLUDE is not defined. Please define it or 'source' the OpenNIDevEnvironment file from the installation)
else ifndef OPENNI2_REDIST
    $(error OPENNI2_REDIST is not defined. Please define it or 'source' the OpenNIDevEnvironment file from the installation)
endif

INC_DIRS += $(OPENNI2_INCLUDE)

include CommonCppMakefile

.PHONY: copy-redist
copy-redist:
	cp -R $(OPENNI2_REDIST)/* $(OUT_DIR)

$(OUTPUT_FILE): copy-redist

