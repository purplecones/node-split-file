# Split File
Split and merge file in multiple parts. Splittable with number of parts or maximum bytes per part

### Splitting file with number of parts
```
splitFile(file, callback(err, names));
```
- file: Path to the file to split.
- callback: 
  - err: Filled with string when error happend. Null for no error.
  - names: Array with full parts paths.

Example:
```javascript
var splitFile = require('./split-file');

splitFile.splitFile(__dirname + '/testfile.bin', 3, function(err, names) {
  console.log(err);
  console.log(names);
});
```

### Splitting file with maximum bytes per part
```
splitFileBySize(file, maxSize, callback(err, names))
```
- file: Path to the file to split.
- maxSize: Max size of the splitted parts. (bytes)
- callback: 
  - err: Filled with string when error happend. Null for no error.
  - names: Array with full parts paths.

Example:
```javascript
var splitFile = require('./split-file');

splitFile.splitFileBySize(__dirname + '/testfile.bin', 457000, function(err, names) {
  console.log(err);
  console.log(names);
});
```

### Merge parts
```
mergeFiles(names, outputFile, callback(err, filename)
```
- names: Input files, array with full part paths.
- outputFile: Full path of the output file.
- callback:
  - err: Filled with string when error happend. Null for no error.
  - filename: The output filename (confirm)


Example:
```javascript
var splitFile = require('./split-file');

splitFile.mergeFiles(names, __dirname + '/testfile-output.bin', function(err, file) {
  console.log(err);
  console.log(file);
});
```


# License
License is MIT, see LICENSE