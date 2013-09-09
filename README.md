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
    <td>
      <code>-s</code>, <code>--source=SOURCE</code></td>
    <td>The folder where unprocessed XML files are stored.</td>
  </tr>
  <tr>
    <td>
      <code>-d</code>, <code>--destination=DESTINATION</code></td>
    <td>The folder where processed XML files will be stored.</td>
  </tr>
  <tr>
    <td>
      <code>-b</code>, <code>--blacklist=BLACKLIST</code></td>
    <td>A text file containing names of XML nodes to be removed.</td>
  </tr>

  <tr>
    <th colspan=2>Optional arguments:</th>
  </tr>
  <tr>
    <td>
      <code>-k</code>, <code>--backup</code></td>
    <td>Will rename the DESTINATION folder before building another copy.</td>
  </tr>
  <tr>
    <td>
      <code>-n</code>, <code>--nuke</code></td>
    <td>
      Will destroy the DESTINATION folder completely before rebuilding it. (Does nothing if <code>--backup</code> is
      also supplied.)
    </td>
  </tr>
  <tr>
    <td>
      <code>-l</code>, <code>--symlink=ACTION</code></td>
    <td>
      The action to take with symbolic links. Can be one of:
      <ul>
        <li><code>file</code> - (default) processes and copies the target files into the DESTINATION folder.</li>
        <li><code>link</code> - copies the links and leaves the target files untouched.</li>
        <li><code>ignore</code> - does not copy symlinks.</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>
      <code>-R</code>, <code>--no-recurse</code></td>
    <td>Will not copy subfolders from SOURCE.</td>
  </tr>

  <tr>
    <th colspan=2>Other options:</th>
  </tr>
  <tr>
    <td>
      <code>-h</code>, <code>--help</code></td>
    <td>Show this message.</td>
  </tr>
</table>
