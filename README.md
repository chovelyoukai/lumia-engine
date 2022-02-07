# About

This is the beginning of my project to create a new engine based on the
QuakeWorld engine. Specifically, I'd like to "modernize" Quake while still
keeping it small, fast, and approachable. There is no concrete plan yet and I'm
still learning how to do the things I want to do.

Specifically, this project is based on TyrQuake, because it seemed to be the
simplest QuakeWorld descendant that would compile with no changes. I removed
all the code for generating NetQuake and the software rendered clients, as well
as things needed to compile for OSX (sorry, Mac users, but I can't afford one.)
I will probably remove the code needed for Windows compilation too just to keep
it simple for now. I also intend to remove all the non-SDL windowing, input,
sound, and etc. code, but I am still studying the engine to see the best way
to do that. The makefile also severely needs simplification - I might just write
a new one.

The major goals are:

- Keep the simplicity and approachability of Quake for modders and mappers.
- Bring all the old jankyness and asset formats into the 21st century.
- Create excellent documentation for game developers and engine hackers.
- Keep the code small and highly performant.
- Ignore backwards compatibility in favor of simplicty and correctness.
- Keep the graphical capabilities simple.
- Keep compatibility with existing level design tools (TrenchBroom is too good
  to even think about giving up.)

Some ideas for the future, once I get everything nice and clean:

- Replace the renderer with one based on modern OpenGL (Vulkan would be neat,
  but that's definitely beyond my skill right now.)
- Add some (very simple) shaders and support for materials, a'la Source VMTs or
  Quake 3 "shaders." Some cool retro effects would be preferable over fancy
  PBR-type fluff.
- Replace the QVM with something better. Some candidates include the Q3VM, a
  LISP dialect, some other interpreted language, etc.
- Update all the file formats:
	- q1bsp -> q3bsp (or maybe something that isn't a BSP at all, are long
	  compile times and faffing about with leaks really necessary in 20XX?)
	- WAD and LMP -> plain old PNGs, JPGs, etc.
	- MDL -> GLTF and OBJ, or something like that.
	- SPR -> ??? (just normal images, I suppose)
	- More audio formats than just WAV.
- See if the networking can be improved. It's already very lean, but Quake 3
  and Source both have more advanced networking that could be drawn from.

# Building

After cloning, `cd` into the `src` directory and simply run `make`. If you want
to run with multiple cores, `make -jX` where `X` is how many cores to use. To
compile with debug symbols, `make DEBUG=Y`. The server (`qwsv`) and client
(`glqwcl`) will be in the `src/bin` folder. You will need SDL2 and its
development files installed.

# Folder structure

The source code of the engine is in `src`. The `src/common` folder contains
code shared between client and server. Client and server-specific code is in
`src/client` and `src/server`, respectively. `src/include` holds various header
files.

When you build the engine, the object files will be inside `src/build` and the
executables will be placed in `src/bin`.

The `tyr` folder contains a bunch of old documents and bits of code from the
original TyrQuake repo that I thought might be useful to keep around.
