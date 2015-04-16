PROJECT_NAME := ble_app_pairing_s110_pca10028

export OUTPUT_FILENAME
MAKEFILE_NAME := $(MAKEFILE_LIST)
MAKEFILE_DIR := $(dir $(MAKEFILE_NAME) ) 

TEMPLATE_PATH = ${NRF_SDK_PATH}/components/toolchain/gcc
ifeq ($(OS),Windows_NT)
include $(TEMPLATE_PATH)/Makefile.windows
else
include $(TEMPLATE_PATH)/Makefile.posix
endif

MK := mkdir
RM := rm -rf

#echo suspend
ifeq ("$(VERBOSE)","1")
NO_ECHO := 
else
NO_ECHO := @
endif

# Toolchain commands
CC       		:= "$(GNU_PREFIX)-gcc"
CXX       		:= "$(GNU_PREFIX)-g++"
AS       		:= "$(GNU_PREFIX)-as"
AR       		:= "$(GNU_PREFIX)-ar" -r
LD       		:= "$(GNU_PREFIX)-g++"
NM       		:= "$(GNU_PREFIX)-nm"
OBJDUMP  		:= "$(GNU_PREFIX)-objdump"
OBJCOPY  		:= "$(GNU_PREFIX)-objcopy"
SIZE    		:= "$(GNU_PREFIX)-size"

# function for removing duplicates in a list
remduplicates = $(strip $(if $1,$(firstword $1) $(call remduplicates,$(filter-out $(firstword $1),$1))))

# c source common to all targets
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/button/app_button.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/sensorsim/sensorsim.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/util/app_error.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/gpiote/app_gpiote.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/timer/app_timer.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/timer/app_timer_appsh.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/scheduler/app_scheduler.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/util/nrf_assert.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/trace/app_trace.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/uart/retarget.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/libraries/fifo/app_fifo.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/drivers_nrf/hal/nrf_delay.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/drivers_nrf/hal/nrf_adc.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/drivers_nrf/pstorage/pstorage.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/drivers_nrf/uart/app_uart_fifo.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/softdevice/common/softdevice_handler/softdevice_handler.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/toolchain/system_nrf51.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/ble_services/ble_bas/ble_bas.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/ble_services/ble_dis/ble_dis.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/ble_racp/ble_racp.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/common/ble_conn_params.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/common/ble_advdata.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/common/ble_srv_common.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/device_manager/device_manager_peripheral.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/components/ble/ble_db_discovery/ble_db_discovery.c
C_SOURCE_FILES += ${NRF_SDK_PATH}/examples/bsp/bsp.c
C_SOURCE_FILES += ./ble_nus.c
C_SOURCE_FILES += ./main.c

# cc source common

#assembly files common to all targets
ASM_SOURCE_FILES  = ${NRF_SDK_PATH}/components/toolchain/gcc/gcc_startup_nrf51.s

# includes common to all targets
INC_PATHS = -I./
INC_PATHS += -I${NRF_SDK_PATH}/components/device/
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_db_discovery
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_debug_assert_handler/
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_error_log/
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_racp
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_services/ble_gls
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_services/ble_bas
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/ble_services/ble_dis
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/common
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/device_manager
INC_PATHS += -I${NRF_SDK_PATH}/components/ble/device_manager/config
INC_PATHS += -I${NRF_SDK_PATH}/components/drivers_nrf/ble_flash/
INC_PATHS += -I${NRF_SDK_PATH}/components/drivers_nrf/hal
INC_PATHS += -I${NRF_SDK_PATH}/components/drivers_nrf/pstorage
INC_PATHS += -I${NRF_SDK_PATH}/components/drivers_nrf/pstorage/config
INC_PATHS += -I${NRF_SDK_PATH}/components/drivers_nrf/uart
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/button
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/sensorsim
INC_PATHS += -I${NRF_SDK_PATH}/components/softdevice/common/softdevice_handler
INC_PATHS += -I${NRF_SDK_PATH}/components/softdevice/s110/headers
INC_PATHS += -I${NRF_SDK_PATH}/components/toolchain
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/fifo
INC_PATHS += -I${NRF_SDK_PATH}/components/toolchain/gcc
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/gpiote
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/scheduler
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/trace
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/timer
INC_PATHS += -I${NRF_SDK_PATH}/components/libraries/util
INC_PATHS += -I${NRF_SDK_PATH}/examples/bsp

OBJECT_DIRECTORY = _build
LISTING_DIRECTORY = $(OBJECT_DIRECTORY)
OUTPUT_BINARY_DIRECTORY = $(OBJECT_DIRECTORY)

# Sorting removes duplicates
BUILD_DIRECTORIES := $(sort $(OBJECT_DIRECTORY) $(OUTPUT_BINARY_DIRECTORY) $(LISTING_DIRECTORY) )

#flags common to all targets
CFLAGS  = -DNRF51
CFLAGS += -DBSP_UART_SUPPORT
CFLAGS += -DBLE_STACK_SUPPORT_REQD
CFLAGS += -DS110
CFLAGS += -DSOFTDEVICE_PRESENT
CFLAGS += -DBOARD_PCA10028
CFLAGS += -mcpu=cortex-m0
CFLAGS += -mthumb -mabi=aapcs
CFLAGS += -Wall -Werror -O3
CFLAGS += -mfloat-abi=soft
# keep every function in separate section. This will allow linker to dump unused functions
CFLAGS += -ffunction-sections -fdata-sections -fno-strict-aliasing
CFLAGS += -flto -fno-builtin
CFLAGS += -DDEBUG
# CFLAGS += -DENABLE_DEBUG_LOG_SUPPORT
CFLAGS += -g

# cxx flags common to all targets
CXXFLAGS = --std=c++11

# keep every function in separate section. This will allow linker to dump unused functions
LDFLAGS += -Xlinker -Map=$(LISTING_DIRECTORY)/$(OUTPUT_FILENAME).map
LDFLAGS += -mthumb -mabi=aapcs -L $(TEMPLATE_PATH) -T$(LINKER_SCRIPT)
LDFLAGS += -mcpu=cortex-m0
# let linker to dump unused sections
LDFLAGS += -Wl,--gc-sections
# use newlib in nano version
LDFLAGS += --specs=nano.specs -lc -lnosys

# Assembler flags
ASMFLAGS += -x assembler-with-cpp
ASMFLAGS += -DNRF51
ASMFLAGS += -DBSP_UART_SUPPORT
ASMFLAGS += -DBLE_STACK_SUPPORT_REQD
ASMFLAGS += -DS110
ASMFLAGS += -DSOFTDEVICE_PRESENT
ASMFLAGS += -DBOARD_PCA10028
#default target - first one defined
default: nrf51422_xxac_s110

#building all targets
all:
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e cleanobj
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e nrf51422_xxac_s110 

#target for printing all targets
help:
	@echo following targets are available:
	@echo 	nrf51422_xxac_s110


C_SOURCE_FILE_NAMES = $(notdir $(C_SOURCE_FILES))
C_PATHS = $(call remduplicates, $(dir $(C_SOURCE_FILES) ) )
C_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(C_SOURCE_FILE_NAMES:.c=.o) )

CC_SOURCE_FILE_NAMES = $(notdir $(CC_SOURCE_FILES))
CC_PATHS = $(call remduplicates, $(dir $(CC_SOURCE_FILES) ) )
CC_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(CC_SOURCE_FILE_NAMES:.cc=.o) )

ASM_SOURCE_FILE_NAMES = $(notdir $(ASM_SOURCE_FILES))
ASM_PATHS = $(call remduplicates, $(dir $(ASM_SOURCE_FILES) ))
ASM_OBJECTS = $(addprefix $(OBJECT_DIRECTORY)/, $(ASM_SOURCE_FILE_NAMES:.s=.o) )

vpath %.c $(C_PATHS)
vpath %.cc $(CC_PATHS)
vpath %.s $(ASM_PATHS)

OBJECTS = $(C_OBJECTS) $(CC_OBJECTS) $(ASM_OBJECTS)

nrf51422_xxac_s110: OUTPUT_FILENAME := nrf51422_xxac_s110
nrf51422_xxac_s110: LINKER_SCRIPT=${NRF_SDK_PATH}/components/softdevice/s110/toolchain/armgcc/armgcc_s110_nrf51422_xxac.ld
nrf51422_xxac_s110: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(LD) $(LDFLAGS) $(OBJECTS) $(LIBS) -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	$(NO_ECHO)$(MAKE) -f $(MAKEFILE_NAME) -C $(MAKEFILE_DIR) -e finalize

## Create build directories
$(BUILD_DIRECTORIES):
	echo $(MAKEFILE_NAME)
	$(MK) $@

# Create objects from C SRC files
$(OBJECT_DIRECTORY)/%.o: %.c
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CC) $(CFLAGS) --std=gnu11 $(INC_PATHS) -c -o $@ $<

# Create objects from CC SRC files
$(OBJECT_DIRECTORY)/%.o: %.cc
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CXX) $(CFLAGS) $(CXXFLAGS) $(INC_PATHS) -c -o $@ $<

# Assemble files
$(OBJECT_DIRECTORY)/%.o: %.s
	@echo Compiling file: $(notdir $<)
	$(NO_ECHO)$(CC) $(ASMFLAGS) $(INC_PATHS) -c -o $@ $<


# Link
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out: $(BUILD_DIRECTORIES) $(OBJECTS)
	@echo Linking target: $(OUTPUT_FILENAME).out
	$(NO_ECHO)$(LD) $(LDFLAGS) $(OBJECTS) $(LIBS) -o $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out


## Create binary .bin file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
$(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex: $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex

finalize: genbin genhex echosize

genbin:
	@echo Preparing: $(OUTPUT_FILENAME).bin
	$(NO_ECHO)$(OBJCOPY) -O binary $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).bin

## Create binary .hex file from the .out file
genhex: 
	@echo Preparing: $(OUTPUT_FILENAME).hex
	$(NO_ECHO)$(OBJCOPY) -O ihex $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).hex

echosize:
	-@echo ""
	$(NO_ECHO)$(SIZE) $(OUTPUT_BINARY_DIRECTORY)/$(OUTPUT_FILENAME).out
	-@echo ""

clean:
	$(RM) $(BUILD_DIRECTORIES) *.jlink

cleanobj:
	$(RM) $(BUILD_DIRECTORIES)/*.o

#### Open JLINK
flash: flash-app

flash-erase-all: flash-erase-all.jlink
	JLinkExe -device nrf51422_xxac flash-erase-all.jlink

flash-app: flash-app.jlink nrf51422_xxac_s110
	JLinkExe -device nrf51422_xxac flash-app.jlink

flash-sd: flash-sd.jlink
	JLinkExe -device nrf51422_xxac flash-sd.jlink

#### Flash Program using JLINK
flash-erase-all.jlink:
	printf "w4 4001e504 2\nw4 4001e50c 1\nsleep 100\nr\nexit\n" > $@

flash-app.jlink:
	printf "w4 4001e504 1\nloadbin ./_build/nrf51422_xxac_s110.bin 0x18000\nr\ng\nexit" > $@

flash-sd.jlink:
	printf "w4 4001e504 1\nloadfile ${NRF_SDK_PATH}/components/softdevice/s110/hex/s110_softdevice.hex 0\nr\ng\nexit" > $@

## Run GDB server
run-debug:
	JLinkGDBServer -noir -device nrf51422_xxaa -if swd -speed 4000 -port 9992

## Generate Documentation
doc: Doxyfile $(C_SOURCE_FILES) $(CC_SOURCE_FILES)
	doxygen Doxyfile
