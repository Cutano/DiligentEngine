
## Current Progress

## v2.3.b

* Core
  * Enabled Vulkan backend on Linux
  * API Changes
    * Implemented separate texture samplers: 
      * Added `UseCombinedTextureSamplers` and `CombinedSamplerSuffix` members to `ShaderCreationAttribs` structure
      * When separate samplers are used (`UseCombinedTextureSamplers == false`), samplers are set in the same way as other shader variables
        via shader or SRB objects
    * Removed `BIND_SHADER_RESOURCES_RESET_BINDINGS` flag, renamed `BIND_SHADER_RESOURCES_KEEP_EXISTING` to `BIND_SHADER_RESOURCES_KEEP_EXISTING`.
	  Added 'BIND_SHADER_RESOURCES_UPDATE_STATIC', 'BIND_SHADER_RESOURCES_UPDATE_MUTABLE', 'BIND_SHADER_RESOURCES_UPDATE_DYNAMIC', and
	  'BIND_SHADER_RESOURCES_UPDATE_ALL' flags
  * Using glslang to compile HLSL to SPIRV in Vulkan backend instead of relying on HLSL->GLSL converter


## v2.3.a

* Core
  * Added `IFence` interface and `IDeviceContext::SignalFence()` method to enable CPU-GPU synchronization
  * Added `BUFFER_MODE_RAW` mode allowing raw buffer views in D3D11/D3D12.
  * Moved `Format` member from `BufferDesc` to `BufferViewDesc`
  * Removed `IsIndirect` member from `DrawAttrbis` as setting `pIndirectDrawAttribs` to a non-null buffer already indicates indirect rendering

* Samples:
  * Added Tutorial 10 - Data Streaming
  * Added Tutorial 11 - Resource Updates

## v2.3

* Core:
  * **Implemented Vulkan backend**
  * Implemented hardware adapter & display mode enumeration in D3D11 and D3D12 modes
  * Implemented initialization in fullscreen mode as well as toggling between fullscreen and windowed modes in run time
  * Added sync interval parameter to ISwapChain::Present()
  * API Changes
    * Added `NumViewports` member to `GraphicsPipelineDesc` struct
    * Removed `PRIMITIVE_TOPOLOGY_TYPE` type
	* Replaced `PRIMITIVE_TOPOLOGY_TYPE GraphicsPipelineDesc::PrimitiveTopologyType` 
      with `PRIMITIVE_TOPOLOGY GraphicsPipelineDesc::PrimitiveTopology`
	* Removed `DrawAttribs::Topology`
    * Removed `pStrides` parameter from `IDeviceContext::SetVertexBuffers()`. Strides are now defined
      through vertex layout.
* API Changes:
  * Math library functions `SetNearFarClipPlanes()`, `GetNearFarPlaneFromProjMatrix()`, `Projection()`,
    `OrthoOffCenter()`, and `Ortho()` take `bIsGL` flag instead of `bIsDirectX`
  * Vertex buffer strides are now defined by the pipeline state as part of the input layout description (`LayoutElement::Stride`)
  * Added `COMMIT_SHADER_RESOURCES_FLAG_VERIFY_STATES` flag
  * Added `NumViewports` member to `GraphicsPipelineDesc` structure
* Samples:
  * Added fullscreen mode selection dialog box
  * Implemented fullscreen mode toggle on UWP with shift + enter
  * Implemented fullscreen window toggle on Win32 with alt + enter
  * Added Tutorial 09 - Quads
* Fixed the following issues:
  * [Add option to redirect diligent error messages](https://github.com/DiligentGraphics/DiligentEngine/issues/9)
  * [Add ability to run in exclusive fullscreen/vsync mode](https://github.com/DiligentGraphics/DiligentEngine/issues/10)

## v2.2.a

* Enabled Win32 build targeting Windows 8.1 SDK
* Enabled build customization through custom build config file
* Implemented PSO compatibility
* Fixed the following issues: 
  * [Messy #include structure?](https://github.com/DiligentGraphics/DiligentEngine/issues/3) 
  * [Move GetEngineFactoryXXXType and LoadGraphicsEngineXXX to Diligent namespace](https://github.com/DiligentGraphics/DiligentEngine/issues/5)
  * [Customizable build scripts](https://github.com/DiligentGraphics/DiligentEngine/issues/6)
  * [Win32FileSystem related functions should use wchar_t (UTF-16)](https://github.com/DiligentGraphics/DiligentEngine/issues/7)

## v2.2

* Added MacOS  and iOS support

## v2.1.b

* Removed legacy Visual Studio solution and project files
* Added API reference
* Added tutorials 1-8

## v2.1.a

* Refactored build system to use CMake and Gradle for Android
* Added support for Linux platform

## v2.1

### New Features

#### Core

* Interoperability with native API
  * Accessing internal objects and handles
  * Creating diligent engine buffers/textures from native resources
  * Attaching to existing D3D11/D3D12 device or GL context
  * Resource state and command queue synchronization for D3D12
* Integraion with Unity
* Geometry shader support
* Tessellation support
* Performance optimizations

#### HLSL->GLSL converter
* Support for structured buffers
* HLSL->GLSL conversion is now a two-stage process:
  * Creating conversion stream
  * Creating GLSL source from the stream
* Geometry shader support
* Tessellation control and tessellation evaluation shader support
* Support for non-void shader functions
* Allowing structs as input parameters for shader functions


## v2.0 (alpha)

Alpha release of Diligent Engine 2.0. The engine has been updated to take advantages of Direct3D12:

* Pipeline State Object encompasses all coarse-grain state objects like Depth-Stencil State, Blend State, Rasterizer State, shader states etc.
* New shader resource binding model implemented to leverage Direct3D12

* OpenGL and Direct3D11 backends
* Alpha release is only available on Windows platform
* Direct3D11 backend is very thoroughly optimized and has very low overhead compared to native D3D11 implementation
* Direct3D12 implementation is preliminary and not yet optimized

### v1.0.0

Initial release