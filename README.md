xml-blacklist
=============

Ruby script to strip nodes from xml documents

# Usage

```
./filter_xml_dir OPTION...
```

Copy all files from one directory to another, stripping out specified XML nodes from each file in the process.

All files from SOURCE will be processed and copied to DESTINATION. Unless `--no-recurse` is supplied, all subfolders will
be copied as well. Only folders with files in them will be copied. File types are not checked. Symlinks are copied into
normal files by default, but with `--symlink=link` the target will be relinked (without change) in DESTINATION, or with
`--symlink=ignore` will be ignored completely.

Files with duplicate names will be overwritten. If `--nuke` is supplied, the entire DESTINATION folder will be destroyed
before rebuilding it; otherwise, non-duplicate files will be kept. If `--backup` is supplied and DESTINATION already
exists, it will first be renamed with a timestamp representing its modification time, and a new folder will be built.

The BLACKLIST file should contain a list of node names to be removed, one name per line. In theory, other CSS selectors
can be used as well, but this has not been tested and should be used with caution.

<table>
  <tr>
    <th colspan=2>Required arguments:</th>
  </tr>
  <tr>
    <td>`-s`, `--source=SOURCE`</td><td>The folder where unprocessed XML files are stored.</td>
  </tr>
  <tr>
    <td>`-d`, `--destination=DESTINATION`</td><td>The folder where processed XML files will be stored.</td>
  </tr>
  <tr>
    <td>`-b`, `--blacklist=BLACKLIST`</td><td>A text file containing names of XML nodes to be removed.</td>
  </tr>

  <tr>
    <th colspan=2>Optional arguments:</th>
  </tr>
  <tr>
    <td>`-k`, `--backup`</td><td>Will rename the DESTINATION folder before building another copy.</td>
  </tr>
  <tr>
    <td>`-n`, `--nuke`</td>
    <td>
      Will destroy the DESTINATION folder completely before rebuilding it. (Does nothing if --backup is also supplied.)
    </td>
  </tr>
  <tr>
    <td>`-l`, `--symlink=ACTION`</td>
    <td>
      The action to take with symbolic links. Can be one of:
      - file - (default) processes and copies the target files into the DESTINATION folder.
      - link - copies the links and leaves the target files untouched.
      - ignore - does not copy symlinks.
    </td>
  </tr>
  <tr>
    <td>`-R`, `--no-recurse`</td><td>Will not copy subfolders from SOURCE.</td>
  </tr>

  <tr>
    <th colspan=2>Other options:</th>
  </tr>
  <tr>
    <td>`-h`, `--help`</td><td>Show this message.</td>
  </tr>
</table>
