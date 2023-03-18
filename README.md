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


 # GLTF-TRANSFORM METHODS

* `center(_options?: CenterOptions): Transform`
* `clearNodeTransform(node: Node): Node`
* `colorspace(options: ColorspaceOptions): Transform`
* `createLayoutPlan(document: Document): LayoutPlan`
* `dedup(_options?: DedupOptions): Transform`
* `dequantize(_options?: DequantizeOptions): Transform`
* `draco(_options?: DracoOptions): Transform`
* `flatten(_options?: FlattenOptions): Transform`
* `getTextureChannelMask(texture: Texture): number`
* `inspect(doc: Document): InspectReport`
* `instance(_options?: InstanceOptions): Transform`
* `join(_options?: JoinOptions): Transform`
* `joinPrimitives(prims: Primitive[], options?: JoinPrimitiveOptions): Primitive`
* `listNodeScenes(node: Node): Scene[]`
* `listTextureChannels(texture: Texture): TextureChannel[]`
* `listTextureInfo(texture: Texture): TextureInfo[]`
* `listTextureSlots(texture: Texture): string[]`
* `meshopt(_options: MeshoptOptions): Transform`
* `metalRough(_options?: MetalRoughOptions): Transform`
* `partition(_options?: PartitionOptions): Transform`
* `prune(_options?: PruneOptions): Transform`
* `quantize(_options?: QuantizeOptions): Transform`
* `reorder(_options: ReorderOptions): Transform`
* `resample(_options?: ResampleOptions): Transform`
* `sequence(_options?: SequenceOptions): Transform`
* `simplify(_options: SimplifyOptions): Transform`
* `sortPrimitiveWeights(prim: Primitive | PrimitiveTarget, limit?: number): void`
* `sparse(_options?: SparseOptions): Transform`
* `tangents(_options?: TangentsOptions): Transform`
* `textureCompress(_options: TextureCompressOptions): Transform`
* `textureResize(_options?: TextureResizeOptions): Transform`
* `unweld(_options?: UnweldOptions): Transform`
* `weldPrimitive(doc: Document, prim: Primitive, options: Required<WeldOptions>): void`
* `weld(_options?: WeldOptions): Transform`
* `transformMesh(mesh: Mesh, matrix: mat4, overwrite?: boolean, skipIndices?: Set<number>):void`
* `transformPrimitive(prim: Primitive, matrix: mat4, skipIndices?: Set<number>): void
    unpartition(_options?: UnpartitionOptions): Transform`
