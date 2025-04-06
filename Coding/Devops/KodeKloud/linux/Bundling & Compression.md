## space

```bash
du -sh path-to-folder-or-file # folder/file disk space used
ls -lh path-to-folder-or-file # actual space it uses
```

- `ls -lh` → **"How many bytes are in this file?"**
- `du -sh` → **"How much disk space is this file/dir actually using?"**

## tar files

- It’s **just a file** (like `.txt` or `.zip`), but with a special structure:
    - Combines multiple files/directories **without compression** by default.
    - Preserves metadata (permissions, timestamps, ownership).

```bash
# bundles the files into test.tar
tar -cf test.tar file1.txt file2.txt 

# lists the files 
tar -tf test.tar

# Extract the contents of the uncompressed tar archive `test.tar` into the current directory.
tar -xf test.tar

# compresses then bundles the files into test.tar.gz
tar -zcf test.tar.gz file1.txt file2.txt

# uncompress then extract
tar -xzf test.tar.gz -C /path/to/destination

# instead of .tar.gz you can also use .tgz
```

## compression
### **bzip2 vs. gzip vs. xz**

|Feature|bzip2 (`.tar.bz2`)|gzip (`.tar.gz`)|xz (`.tar.xz`)|
|---|---|---|---|
|**Flag**|`-j`|`-z`|`-J`|
|**Speed**|Slow|Fast|Slowest|
|**Ratio**|Better|Good|Best|
|**Use Case**|Balance of size/speed|Quick archives|Max compression|

## uncompression
```bash
gunzip xxx.gz

gunzip xxx.tar.gz # uncompresses
tar -xf xxx.tar # extracts

tar -zxf xxx.tar.gz # uncompresses then extracts
```