# bin2abs
Quick utility to convert a pure PDP-11 binary to Absolute Loader format.

The PDP-11 input binary is prepended with a size byte header, two byte signature, 0x01, 0x00. Then followed by the length
of the input file + the size of the header (6 bytes). Then the start address of the binary which will be where the loader wil store the input proram.

After bin2abs has copied the data it will append a checksum which is the two's complement of the module 256 sum o all bytes including the size byte header.

SimH loader doesn't allow loading of absolute loader files which doesn't have a start record. We then append a dummy record to make SimH happy.