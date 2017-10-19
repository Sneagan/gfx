Hello stranger! If you found gfx-rs interesting, especially the new Hardware Abstraction Layer stuff and friends, here is a place to get you started on the track to become a part of our community, contributing for the better future of Rust graphics and beyond.

### First steps

  1. Make sure to have the late-ish Rust stable installed on the platform of your choice.
  2. Check out gfx-rs and type `make` in the repository root in order to ensure that everything is building. Skip this step if you are on Windows without Subsystem for Linux.
  3. Run the hal/quad example `(cd example/hal/quad && cargo run --feature <backend>)` where the `<backend>` is `vulkan`, `dx12`, or `metal`.
  4. Navigate through the project code to get familiar with the style and structure.

### Big tasks

Now that we explained how to [draw an owl](http://i0.kym-cdn.com/photos/images/original/000/572/078/d6d.jpg), let's dive into the current development targets, where extra help would be most useful:

  - Polish and improve existing HAL backends: Vulkan, D3D12, and Metal - all miss a ton of features, don't nearly validate as much as they could, and need more testing.
  - OpenGL backend: roughly 1/3 of the way. We need GL ES 3.1 target to perform efficiently.
    - bonus points for making it work on Android/iOS
    - extra credit for Emscripten compatibility
  - [Warden](https://github.com/gfx-rs/gfx/pull/1589) test framework:
    - add support for missing features
    - write more tests
    - set up headless GL testing on CI (depends on GL to be available)
  - [WebGPU prototype](https://github.com/kvark/webgpu-servo): needs overall architecture review, IPC logic rewrite, many basic improvements to fit the portability and security requirements of the Web.
    - WebAssembly compatibility investigation
    - extra bonus for taking a peek at [rspirv](https://github.com/google/rspirv) addressing some of the issues there. We hope to eventually use Rust for shader sanitation and translation, while currently using SPIRV-Cross.
  - [Vulkan Portability](https://github.com/kvark/portability) prototype: the beginning is there, way more needs to be done. This is supposed to be more of a mechanical task, with major concerns resolved conceptually. End goals are:
    - hook up to Ash, Vulkano, C applications of your choice
    - pass Khronos conformance test suite
  - `gfx-render` layer: needs more design work before the implementation, probably the most difficult of all.
    - port all the old examples to be runnable again
