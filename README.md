# Hakkei ZMK demo config

The `config` directory is a ZMK configuration dir; as built,
it's got all the custom files to build a firmware for the ST Micro
P-NUCLEO-WB55 board.  The files in this directory, combined with the
standard ZMK distribution, are sufficient to build a firmware for a
3-button shield (the `uno_trio`), which is wired as three keys in an
active-low configuration.  The three keys should be wired to
"D0", "D1", and "D2" of the dev board.  It's been tested over USB;
it builds with BLE support, but no testing there has been done.

To build, you need to check out the ZMK repo according to the
following: https://zmkfirmware.dev/docs/development/setup .  You'll
need to make sure `ZEPHYR_TOOLCHAIN_VARIANT` and `GNUARMEMB_TOOLCHAIN_PATH`
are set in the environment;  `ZEPHYR_TOOLCHAIN_VARIANT` should be set to
`gnuarmemb`, and `GNUARMEMB_TOOLCHAIN_PATH` should be set to the path
where the toolchain is installed.

Once ZMK is set up according to the above instructions, you'll need the
full path to the `config` directory in this repo:

```export ZMK_CONFIG_DIR=/path/to/this/repo/config
```

To build, `cd` into the `zmk/app` directory, and use the `west` build tool:

```cd /path/to/zmk/app
west build -b nucleo_wb55rg -- -DSHIELD=uno_trio -DZMK_CONFIG=${ZMK_CONFIG_DIR}
```

If the build succeeds, and you have OpenOCD installed (you'll need to build the
latest OpenOCD from git - the 0.10.0 release doesn't have full support for the
STM32WB55), you can flash the board with `west flash`.
