# Parallel md5sum or sha256sum or sha1sum or sha512sum

Compute and verify checksums like `md5sum`, but 64 times faster (if you have 64 cores, fast memory and many files).

### Installation

```bash
wget https://raw.githubusercontent.com/99991/parallel-md5sum/refs/heads/main/md5sum
chmod u+x md5sum
```

### Compute md5 checksums for files in current directory

```bash
./md5sum *
```

### Write checksums to `checksums.txt`

```bash
./md5sum * > checksums.txt
```

### Verify checksums

```bash
./md5sum -c checksums.txt
```

### Compute md5sum of the word "duck"

```bash
printf "duck" | ./md5sum
```

### Compute sha256sum

```bash
./md5sum --mode sha256 *
```

### Help

```
$ ./md5sum --help
usage: md5sum [OPTION]... [FILE]...

Print or check md5 (128-bit) checksums.

options:
  -h, --help            show this help message and exit
  -c [CHECK], --check [CHECK]
                        read md5 sums from the FILEs and check them                                    
  -m       {md5,sha384,md5-sha1,blake2b,sha1,sha256,sha3_256,shake_128,sha512_256,sha3_512,sha512,sha3_384,sha224,shake_256,ripemd160,blake2s,sha512_224,sha3_224,sm3},
  --method {md5,sha384,md5-sha1,blake2b,sha1,sha256,sha3_256,shake_128,sha512_256,sha3_512,sha512,sha3_384,sha224,shake_256,ripemd160,blake2s,sha512_224,sha3_224,sm3},
  --mode   {md5,sha384,md5-sha1,blake2b,sha1,sha256,sha3_256,shake_128,sha512_256,sha3_512,sha512,sha3_384,sha224,shake_256,ripemd160,blake2s,sha512_224,sha3_224,sm3}                         
                        hash algorithm to use
```

### sha256sum or sha1sum or sha512sum or ...

You can change the default hashing method by changing the line

```python
METHOD = "md5"
```
in `md5sum` to

```python
METHOD = "sha256"
```

to get the behavior of `sha256sum` or other hashing programs.

### Missing options

The following options are not implemented:

* `--binary` or `--text` (everything is assumed to be binary)
* `--ignore-missing`
* `--quiet`
* `--status`
* `--strict`
