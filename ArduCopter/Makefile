
name1 := $(lastword $(MAKEFILE_LIST))

include pix.mk

name3 := $(lastword $(MAKEFILE_LIST))

include ./src/inc.mk

name2 := $(lastword $(MAKEFILE_LIST))

SYSTYPE := $(shell uname)

ifneq ($(findstring CYGWIN, $(SYSTYPE)),) 
  MK_DIR := $(shell cygpath -m ../mk)
else
  MK_DIR := $(patsubst %/,%,$(dir $(lastword $(MAKEFILE_LIST))))
endif
include $(MK_DIR)/environ.mk	
$(info Reading $(LANG))
$(info Reading $(SYSTYPE))
$(info Reading $(GIT_VERSION))
$(info Reading $(EXTRAFLAGS))
$(info Reading $(SRCROOT))
$(info Reading $(SKETCHBOOK))
$(info Reading $(SKETCH))
$(info Reading $(BUILDROOT))
$(info Reading $(MAKECMDGOALS))
$(info Reading $(APPDIR))
$(info Reading $(HAL_BOARD))
$(info Reading $(HAL_BOARD_SUBTYPE))
px4-v2:
	@echo name1 = $(name1)
	@echo name2 = $(name2)
	@echo name3 = $(name3)
	@echo $(MAKEFILE_LIST)
	@echo $(SYSTYPE)
	@echo $(MK_DIR)
GIT_VERSION ?= $(shell git rev-parse HEAD | cut -c1-8)
EXTRAFLAGS += -DGIT_VERSION="\"$(GIT_VERSION)\""

# Add missing parts from libc and libstdc++ for all boards
EXTRAFLAGS += -I$(SKETCHBOOK)/libraries/AP_Common/missing
px4:
	@echo $(GIT_VERSION)
	@echo $(EXTRAFLAGS)