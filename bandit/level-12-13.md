# [Level 12 to 13](https://overthewire.org/wargames/bandit/bandit13.html)

- Exercise: The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv
- Background:
  - In a hex dump, each byte (8 bits) is represented as a two-digit hexadecimal number. Hex dumps are commonly organized into rows of 8 or 16 bytes, sometimes separated by whitespaces.
  - grep - searches for patterns in each file
  - sort - sort lines of text files
  - uniq - report or omit repeated lines
  - strings - print the sequences of printable characters in files
  - base64 - base64 encode/decode data and print to standard output
  - tr - translate or delete characters
  - tar - an archiving utility
  - gzip - compress or expand files
  - bzip2 - a block-sorting file compressor
  - xxd - make a hex dump or do the reverse
  - mkdir - make directories
  - cp - copy files and directories
  - mv - move (rename) files
  - file - determine file type
- Solution:
	1. mktemp -d -> /tmp/tmp.TvEfmJqj4u
	2. cp data.txt /tmp/tmp.TvEfmJqj4u
	3. cd /tmp/tmp.TvEfmJqj4u
	4. First line of data.txt: 1f8b... -> [Signature](https://en.wikipedia.org/wiki/List_of_file_signatures) : gz/tar.gz file
	5. xxd -r data.txt data (make reverse of hexdump and safe result in data)
	6. mv data data.gz
	7. gzip -d data.gz
	8. xxd data -> 425a Signature: bz2
	9. mv data data.bz2
	10. bzip2 -d data.bz2
	11. xxd data -> Back to the beginning: 1f8b (That means I choose the wrong ending (gz) in the beginning, so let's try with tar.gz)
	12. mv data data.tar.gz
	13. tar -xf data.tar.gz
	14. xxd data5.bin | head -> 6461 7461 Signature: not found
	15. file data5.bin -> POSIX tar archive
	16. tar -xf data5.bin
	17. file data6.bin -> bzip compressed file
	18. xxd data6.bin.out | head -> 6461 7471...data8.bin Signature
	19. tar -xf data6.bin.out
	20. xxd data8.bin -> 1f8b Signature
	21. file data8.bin
	22. mv data8.bin data8.gz
	23. gzip -d data8.gz
	24. cat data8
- Password: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
