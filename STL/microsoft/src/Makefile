IDACLANG_ARGS += --idaclang-log-all
IDACLANG_ARGS += --idaclang-tilname $(TIL_NAME)
IDACLANG_ARGS += --idaclang-tildesc $(TIL_DESC)
CLANG_ARGV += -ferror-limit=50
TIL_NAME = msstl
TIL_DESC = "Microsoft STL headers for windows"
INPUT_FILE = msstl.h
MSSTL_SRC = "./STL"


CLANG_ARGV = -target arm-pc-win32                \
             -x c++                                    \
			 -I$(MSSTL_SRC)/stl/inc
IDACLANG = "/mnt/e/IDA_Pro_v7.5_Portable/idaclang.exe" 

all: $(TIL_NAME)
.PHONY: all $(TIL_NAME) clean
$(TIL_NAME): $(TIL_NAME).til

$(TIL_NAME).til: $(INPUT_FILE)
	$(IDACLANG) $(IDACLANG_ARGS) $(CLANG_ARGV) $(INPUT_FILE) > $(TIL_NAME).log

clean:
	rm -rf *.til *.log

