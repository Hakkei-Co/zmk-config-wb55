The shield in this directory was created to test
a basic matrix keyboard.  It's a 5x2 matrix, set up to be wired
to a Nucleo WB55 dev board, with default solder
bridges, to the following pins:

row1 to PA4 (Arduino connector pin D10, which is also CN10 pin 17)
row2 to PA5 (Arduino connector pin D13, which is also CN10 pin 11)

col1 to PB0 (CN10 pin 22)
col2 to PB1 (CN10 pin 24)
col3 to PB2 (CN7 pin 2)
col4 to PB13 (CN10 pin 30)
col5 to PB4 (CN10 pin 4)

Diodes are wired as "col2row", which means the cathodes are wired
together in the rows.
