#  Compression & Archive Commands
Compression and archive commands are used to combine multiple files into a single archive and reduce file size for storage, backup, and file transfer.

# 1. tar
Creates or extracts archive files.

# Create Archive

```bash
tar -cvf backup.tar Documents/
```

## Options

 `c` → Create a new archive.

 `v` → Verbose mode (displays files being processed).

 `f` → Specifies the archive file name.

## Extract Archive

```bash
tar -xvf backup.tar
```

## Options

 `x` → Extract an archive.

 `v` → Verbose mode.

 `f` → Specifies the archive file name.

# 2. gzip
Compresses a file into `.gz` format.

# Syntax

```bash
gzip filename
```
## Example

```bash
gzip backup.tar
```

# Output

```text
backup.tar.gz
```

# 3. gunzip
Decompresses a `.gz` file.

# Syntax

```bash
gunzip filename.gz
```

# Example

```bash
gunzip backup.tar.gz
```

# Output

```text
backup.tar
```
# 4. zip
Creates a ZIP archive.

# Syntax

```bash
zip archive_name.zip file1 file2
```

# Example

```bash
zip files.zip report.txt notes.txt
```
# 5. unzip
Extracts files from a ZIP archive.

# Syntax

```bash
unzip archive_name.zip
```

# Example

```bash
unzip files.zip
```
# 6. bzip2
Compresses a file using the **bzip2** compression algorithm.

# Syntax

```bash
bzip2 filename
```

# Example

```bash
bzip2 report.txt
```

# Output

```text
report.txt.bz2
```
# 7. bunzip2
Decompresses a `.bz2` file.

# Syntax

```bash
bunzip2 filename.bz2
```

# Example

```bash
bunzip2 report.txt.bz2
```


# Summary

| Command | Description |
|---------|-------------|
| `tar` | Creates or extracts archive files. |
| `gzip` | Compresses a file into `.gz` format. |
| `gunzip` | Decompresses a `.gz` file. |
| `zip` | Creates a ZIP archive. |
| `unzip` | Extracts files from a ZIP archive. |
| `bzip2` | Compresses a file using the bzip2 algorithm. |
| `bunzip2` | Decompresses a `.bz2` file. | table format