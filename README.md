# iqm.zig
A simple (and incomplete) IQM importer written in Zig

> **NOTE:** As the title says, this is *INCOMPLETE* and thus *not really useful for anything but basic IQM file loading*

### How to setup:
- Download the `iqm.zig` file and `@import()` it up!

### Code example:
```zig
const iqm = @import("iqm.zig");

var model_raw = @embedFile("model.iqm");
var model = try iqm.readBuffer(model_raw, false, allocator_of_choice);
var mesh = model.meshes[0];

try renderer.renderMesh(model, mesh);
```

### Documentation:
- **`readBuffer(data: []const u8, isEXM: bool, alloc: std.mem.Allocator) !Model`**:
<br>&emsp;Creates a Model struct out of `data` which could return an error at handling memory, reading the header or finding invalid data.

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
- [ ] Big endian support
