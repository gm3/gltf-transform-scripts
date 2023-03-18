# gltf-transform-scripts

This will remove all extensions from a folder of .glbs

save as convert.js, use node and gltf-transform/core

```
const { Document, NodeIO } = require('@gltf-transform/core');
const fs = require('fs');

async function removeVRMExtension(file) {
  // Load glTF file.
  const io = new NodeIO(fs);
  const doc = await io.read(file);

  // Remove VRM extension from the glTF model.
  const root = doc.getRoot();
  const extensions = root.listExtensions();
  if (extensions.includes('VRM')) {
    root.removeExtension('VRM');
  }

  // Save modified glTF file.
  await io.write(file, doc);
  console.log(`${file} has been processed.`);
}

// Remove VRM extension from all glTF files in the current directory.
const files = fs.readdirSync('./');
for (const file of files) {
  if (file.endsWith('.glb') || file.endsWith('.gltf')) {
    removeVRMExtension(file);
  }
}
```
