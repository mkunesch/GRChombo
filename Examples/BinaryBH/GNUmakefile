# -*- Mode: Makefile -*-

### This makefile produces an executable for each name in the `ebase'
###  variable using the libraries named in the `LibNames' variable.

# Included makefiles need an absolute path to the Chombo installation
# CHOMBO_HOME := Please set the CHOMBO_HOME locally (e.g. export CHOMBO_HOME=... in bash)

ifndef GRCHOMBO_SOURCE
    $(error Please define GRCHOMBO_SOURCE - see installation instructions.)
endif


ebase := Main_BinaryBH

LibNames := AMRTimeDependent AMRTools BoxTools

src_dirs := $(GRCHOMBO_SOURCE)/utils \
            $(GRCHOMBO_SOURCE)/simd  \
            $(GRCHOMBO_SOURCE)/CCZ4  \
            $(GRCHOMBO_SOURCE)/BoxUtils  \
            $(GRCHOMBO_SOURCE)/GRChomboCore  \
            $(GRCHOMBO_SOURCE)/AMRInterpolator  \
            $(GRCHOMBO_SOURCE)/TaggingCriteria  \
            $(GRCHOMBO_SOURCE)/InitialConditions/BlackHoles

SimulationParameters.hpp: SimulationParameters.inc

SimulationParameters.inc: SimulationParameters.txt
	python $(GRCHOMBO_SOURCE)/utils/generate_parameter_code.py SimulationParameters.txt SimulationParameters.inc

clean::
	rm -rf $(ebase)*.dSYM
	rm SimulationParameters.inc

include $(CHOMBO_HOME)/mk/Make.test
