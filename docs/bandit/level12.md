# Level 12

Login with `bandit12` and the password.

The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under `/tmp` in which you can work using `mkdir`. For example: mkdir `/tmp/myname123`. Then copy the datafile using `cp`, and rename it using `mv` (read the manpages!).

	bandit12@bandit:~$ mkdir /tmp/7a8dsfyiuhakj
    bandit12@bandit:~$ cd /tmp/7a8dsfyiuhakj
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ cp ~/data.txt .
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ head data.txt
    00000000: 1f8b 0808 d7d2 c55b 0203 6461 7461 322e  .......[..data2.
    00000010: 6269 6e00 013c 02c3 fd42 5a68 3931 4159  bin..<...BZh91AY
    00000020: 2653 591d aae5 9800 001b ffff de7f 7fff  &SY.............
    00000030: bfb7 dfcf 9fff febf f5ad efbf bbdf 7fdb  ................
    00000040: f2fd ffdf effa 7fff fbd7 bdff b001 398c  ..............9.
    00000050: 1006 8000 0000 0d06 9900 0000 6834 000d  ............h4..
    00000060: 01a1 a000 007a 8000 0d00 0006 9a00 d034  .....z.........4
    00000070: 0d1a 3234 68d1 e536 a6d4 4000 341a 6200  ..24h..6..@.4.b.
    00000080: 0069 a000 0000 0000 d003 d200 681a 0d00  .i..........h...
    00000090: 0001 b51a 1a0c 201e a000 6d46 8068 069a  ...... ...mF.h..

I believe that both `xxd` and `hexdump` support reading hexdumps. The manpage confirms this.

    bandit12@bandit:/tmp/7a8dsfyiuhakj$ xxd -r data.txt > out

I use `file` to see what kind of compression this is.

    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out
    out: gzip compressed data, was "data2.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ gzip -cd out > out2
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out2
    out2: bzip2 compressed data, block size = 900k
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ bzip2 -cd out2 > out3
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out3
    out3: gzip compressed data, was "data4.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ gzip -cd out3 > out4
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out4
    out4: POSIX tar archive (GNU)
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ tar -xvf out4
    data5.bin
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file data5.bin
    data5.bin: POSIX tar archive (GNU)
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ tar -xvf data5.bin
    data6.bin
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file data6.bin
    data6.bin: bzip2 compressed data, block size = 900k
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ bzip2 -cd data6.bin > out7
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out7
    out7: POSIX tar archive (GNU)
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ tar -xvf out7
    data8.bin
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file data8.bin
    data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 16 12:00:23 2018, max compression, from Unix
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ gzip -cd data8.bin > out9
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ file out9
    out9: ASCII text
    bandit12@bandit:/tmp/7a8dsfyiuhakj$ cat out9
    The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
