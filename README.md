# iqm.zig
A simple (and incomplete) IQM importer written in Zig

> **NOTE:** As the title says, this is *INCOMPLETE* and thus *not really useful for anything but basic IQM file loading*

### How to setup:
- Download the `iqm.zig` file and `@import()` it up in your project! *It has no other dependency than the Zig Standard Library itself*.

### Code example:
```zig
const iqm = @import("iqm.zig");

var modelA_raw = @embedFile("assets/modelA.iqm");
var modelA = try iqm.fromBuffer(model_raw, false, allocator_of_choice);
var modelB = try iqm.fromFile("assets/modelB.iqm", null, allocator_of_choice);

var meshA = modelA.meshes[0];
var meshB = modelB.meshes[0];

try renderer.renderMesh(modelA, meshA);
try renderer.renderMesh(modelB, meshB);
```

### Documentation:
- **`fromBuffer(data: []const u8, isEXM: bool, alloc: std.mem.Allocator) !Model`**:
<br>&emsp;Creates a `Model` struct out of `data` which could return an error at handling memory, reading the header or finding invalid data.

- **`fromFile(name: []const u8, isEXM: ?bool, alloc: std.mem.Allocator) !Model`**:
<br>&emsp;Creates a `Model` struct out of the file specified by `name` (relative to `CWD`) which could return an error at handling memory, reading the header or finding invalid data. `isEXM` will be true if `null` and `name` ends with `.exm`


### Roadmap:
- [X] Vertex arrays
- [X] Vertex indices/triangles
- [X] Texts
- [ ] Materials
- [ ] Poses/Animations
- [X] Meshes
- [ ] EXM data 

#### Extra roadmap:
- [ ] Basic OpenGL renderer example
- [ ] C Exports
  - [ ] Basic OpenGL C renderer example
  - [ ] C++ "bindings" or whatever they're named
- [ ] Big endian support

### Anti-roadmap (things that wont get implemented):
- IQM/EXM Exporting.


### License:
This project is covered under the ZLIB License and the license is bundled with the library, check out `iqm.zig`.
