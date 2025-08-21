# MSFS Livery Creation Toolchain


This Repo provides Links and Instructions for effective MSFS 2020 /2024 Livery creation.
Please note this document does not describe the official process intended by Microsoft / Asobo but a Workflow used by several livery painters to exelarate the process.
This Toolchain uses Freeware and public Tools only

## Used Tools

- MSFS SDK [download instructions](https://docs.flightsimulator.com/html/Introduction/SDK_Overview.htm)
- Blender (v4.1) [downlaod link](https://download.blender.org/release/Blender4.1/)
- Gimp [download link](https://www.gimp.org/downloads/)
- NVIDIA Texture Tools Exporter [downlaod link](https://developer.nvidia.com/texture-tools-exporter)
- Model Converter X [download link](https://www.scenerydesign.org/modelconverterx/)
- msfs2blender2msfs [github](https://github.com/flybywiresim/msfs2blender2msfs)
- msfs2blend [github](https://github.com/bestdani/msfs2blend)
- ImageToMSFSKTX2 [github](https://github.com/theflaknine/ImageToMSFSKTX2)

## Steps

### Paintkit cration (2020)
1. Find model.gltf in your addons directory or the Official directory (e.g. "...\AppData\Roaming\Microsoft Flight Simulator\Packages\Official\Steam\...")
2. Select external model.gltf, select lowest LOD possible, also copy any .bin file is present
3. import model into blender using msfs2blend (File -> import -> MSFS GLTF (.gltf))
4. Hide all unwanted meshes (ctrl + H) using Layout Mode
5. Create Textures for selected Mesh in Textrue Paint Mode (Material -> Base Color -> Image Texture)

### Paintkit cration (2024 Native)
1. Start MSFS2024
2. Enable Dev Mode (Settings -> Advanced -> Dev Mode on)
3. Enable [VFS Projector](https://docs.flightsimulator.com/msfs2024/html/2_DevMode/Menus/Tools/The_Virtual_File_System.htm?agt=index) (Dev Pannel -> Tools -> VFS Projector)
4. Navigate to VFS path in explorer (e.g.: "...\AppData\Roaming\Microsoft Flight Simulator 2024\VFSProjection\simobjects\airplanes")
5. model con be found in common or in attachments/external
6. Select and **COPY** external model.gltf, select lowest LOD possible (LOD0 might be locked), also copy any .bin file is present
7. Import model.gltf file in Model Converter X, Export Model as MSFS2020 gltf format (new name e.g.: "model_2020.gltf")
8. import model into blender using default GLTF support (**not msfs2blend**) (File -> import -> glTF 2.0 (.glb .gltf))
9. repeat for all attachments until model is complete
4. Hide all unwanted meshes (ctrl + H) using Layout Mode
5. Create Textures for selected Mesh in Textrue Paint Mode (Material -> Base Color -> Image Texture)

### MSFS 2024 Template Texture creation
1. Find white base textures .PNG.KTX2 files found in common or in attachments/external
2. Open KTX2 in NVIDIA Texture Tools Exporter
3. apply Effects -> Effect: sRGB to Linear
4. Export File as .PNG

### MSFS 2024 KTX2 Texture Conversion
1. Copy all .PNG Textures to ImageToMSFSKTX2 ALDB directory (or COMP or Detail ...)
2. execute "Image to MSFS KTX2.bat" and select Option 2, and 4 (MSFS2024 must not be running, try several times if OUTPUT dir stays empty, try 4 second delay)
3. .KTX2 Files are copied to OUTPUT directory

### Generate DDS files using Gimp
1. Open existing .PNG.DDS file (helps to load correct file config)
2. Apply Livery.png file onto White Texture Template (use Multiply Mode for Layer)
3. Merge down all loayers
4. Export as DDS File (File -> Export As ..., name .png.dds, select Compression BC3 / DXT5, Mipmaps: Genrate Mipmaps)

### Thumbnail creation 2020
1. Start MSFS 2020
2. enable Dev Mode using Settings
3. goto Hangar View
4. execute Dev -> Tools -> Thumbnail Capture Tool
5. load General Preset
6. select "Make Unique"
7. execute capture

### Thumbnail creation 2020
1. Start MSFS 2024
2. enable Dev Mode using Settings
3. Select Livery and Load into the game
4. load or create an empty Project (I reuse a dummy)
5. execute Dev -> Tools -> Thumbnail Capture Tool
6. load General Preset
7. delete all but Thumbnail, Thumbnail (transparent), Front Right (transparent), Right (transparent)
8. select "Make Unique"
9. execute capture


## Tips for Beginers:

- to get the correct file structure for livereies base your livery on a template or existing Livery and adapt the name in: aircraft.cfg, layout.json (with tool), manifest and texture.name directories.
- Do not directly paint on a white livery, this destroys details. Paint on a white canvas instead and Multyply with the white base livery at the end.
- Add a 3 - 5 pixel border arround your UV surfaces to avoid white line artifacts on lower LODs.
- convert KTX2 Textures from sRGB to Linear on export to avoid washed out colors.
- Use Blender Texture Stencil to Apply Logos, Texts and Decals
- Do not overwrite the Metallic Details with your Livery on a base texture. Those are often grey on the ALBD texture and blue/pink on the COMP.

## Usefull Videos and Tutorials:

KTX2 Conversion: [EzRyder MSFS 2024 KTX2 - PNG Texture Conversion](https://www.youtube.com/watch?v=-_y8enhqXi4)  
Blender Basics: [bestdani Microsoft Flight Simulator (FS2020) - 3D Livery Painting for free!](https://www.youtube.com/watch?v=SZCe_x-V9co)
VFS Projector: [MSFS 2024 VFS Projector and Server Files](https://www.youtube.com/watch?v=bdNqYiP_ie4)

