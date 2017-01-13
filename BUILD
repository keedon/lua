LIB_COMPILER_FLAGS=[
	"-D_SUSV2_SOURCE",
	"-D_POSIX_SOURCE",
	"-D_LIMITS_EXTENSION",
	"-D_BSD_SOURCE",
	"-D_BSD_EXTENSION",
	"-DHAVE_SOCK_OPTS",
	"-DLUA_USE_C89",
	"-DLUA_USE_LONGJMP",
	"-D__HARVEY__",
	"-O2",
	fmt("-I%s/amd64/include", env("APEX")),
	fmt("-I%s/include", env("APEX")),
	"-mno-red-zone",
	"-ffreestanding",
	"-fno-builtin",
	"-nostdinc",
	"-trigraphs",
	"-Wall",
	"-Wuninitialized",
	"-g" 
]

CMD_LINK_OPTS = [
	fmt("%s/amd64/lib/crt1.o", env("APEX")),
	fmt("%s/amd64/lib/crti.o", env("APEX")),
	fmt("%s/amd64/lib/crtn.o", env("APEX")),
	"-lap",
	"-lc",
	"-llua",
	fmt("-L%s/amd64/lib", env("APEX")),
	fmt("-L%s/amd64/lib", env("HARVEY")),
	"-L./build_out/lib",
	"-static",
	"-nostdlib",
]

CC_INCLUDES = [
        "//",
        "$APEX/amd64/include",
        "$APEX/include",
        "$HARVEY/sys/include",
]

cc_binary(
	name="lua",
	deps=[
		":liblua"
	],
	srcs=[
		"lua.c"
	],
        copts = LIB_COMPILER_FLAGS,
	linkopts=CMD_LINK_OPTS
)


cc_library(
	name = "liblua",
        copts = LIB_COMPILER_FLAGS,
        includes=CC_INCLUDES,
	srcs = [
                "lapi.c",
                "lcode.c",
                "lctype.c",
                "ldebug.c",
                "ldo.c",
                "ldump.c",
                "lfunc.c",
                "lgc.c",
                "llex.c",
                "lmem.c",
                "lobject.c",
                "lopcodes.c",
                "lparser.c",
                "lstate.c",
                "lstring.c",
                "ltable.c",
                "ltm.c",
                "lundump.c",
                "lvm.c",
                "lzio.c",
                "lauxlib.c",
                "lbaselib.c",
                "lbitlib.c",
                "lcorolib.c",
                "ldblib.c",
                "liolib.c",
                "lmathlib.c",
                "loslib.c",
                "lstrlib.c",
                "ltablib.c",
                "lutf8lib.c",
                "loadlib.c",
                "linit.c"
	]
)

