parse-wavefront-obj
===================
### Wavefront OBJ parser

Parses a [Wavefront OBJ](http://en.wikipedia.org/wiki/Wavefront_.obj_file) string or buffer. If you're looking for a stream parser check [this](https://github.com/mikolalysenko/parse-obj).

Supports vertex normals and UV coordinates. Doesn't support material libraries (though I'm open to PRs), nor multiple meshes embedded in the same file.

Install
-------

```bash
$ npm install parse-wavefront-obj
```

Usage
-----

```javascript
var parseOBJ = require('parse-wavefront-obj');
var fs = require('fs');

var buf = fs.readFileSync('mesh.obj');
var mesh = parseOBJ(buf);

console.log(mesh);
/*
{
  positions: [...],
  cells: [...],

  // The following attributes are available when defined 
  // in the original file

  vertexUVs: [...],     // array of UV coordinates
  faceUVs: [...],       // array of UV indices
  vertexNormals: [...], // array of vertex normals
  faceNormals: [...],   // array of normal indices
  name: 'foo'           // mesh name
}
*/
```