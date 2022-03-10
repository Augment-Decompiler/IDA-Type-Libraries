IDACLANG_ARGS += --idaclang-log-all
IDACLANG_ARGS += --idaclang-tilname $(TIL_NAME)
IDACLANG_ARGS += --idaclang-tildesc $(TIL_DESC)
CLANG_ARGV += -ferror-limit=50
TIL_NAME = msstl
TIL_DESC = "Microsoft STL headers for Linux"
INPUT_FILE = msstl.h
MSSTL_SRC = "./STL"
CLANG_ARGV = -target x86_64-pc-win32                   \
             -x c++                                    \
			 -I$(MSSTL_SRC)/stl/inc
IDACLANG = "" 

all: $(TIL_NAME)
.PHONY: all $(TIL_NAME) clean
$(TIL_NAME): $(TIL_NAME).til

$(TIL_NAME).til: $(INPUT_FILE)
	$(IDACLANG) $(IDACLANG_ARGS) $(CLANG_ARGV) $(INPUT_FILE) > $(TIL_NAME).log

clean:
	rm -rf *.til *.log

