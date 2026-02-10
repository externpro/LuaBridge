# LuaBridge dependencies

|project|license [^_l]|description [dependencies]|version|source|diff [^_d]|
|-------|-------------|--------------------------|-------|------|----------|
|<a id='luabridge' />[luabridge](http://vinniefalco.github.io/LuaBridge/Manual.html 'LuaBridge Reference Manual')|[MIT](https://github.com/vinniefalco/LuaBridge/#official-repository 'MIT License')|a lightweight, dependency-free library for binding Lua to C++ [deps: _lua_]| |[upstream](https://github.com/vinniefalco/LuaBridge 'github.com/vinniefalco/LuaBridge')|  [patch]|
|<a id='lua' />[lua](http://www.lua.org/)|[MIT](http://www.lua.org/license.html 'MIT License')|a powerful, fast, lightweight, embeddable scripting language|[xpv5.2.3.3](https://github.com/externpro/lua/releases/tag/xpv5.2.3.3 'release')|[repo](https://github.com/externpro/lua 'github.com/externpro/lua') [upstream](https://github.com/lua/lua 'github.com/lua/lua')|[diff](https://github.com/externpro/lua/compare/v5.2.3...xpv5.2.3.3 'github.com/externpro/lua/compare/v5.2.3...xpv5.2.3.3') [patch]|

![deps](xprodeps.svg 'dependencies')

Dependency version check: all 1 parent-manifest versions match pinned versions.

|diff  |description|
|------|-----------|
|patch |diff modifies/patches existing cmake|
|intro |diff introduces cmake|
|auto  |diff adds cmake to replace autotools/configure/make|
|native|diff adds cmake but uses existing build system|
|bin   |diff adds cmake to repackage binaries built elsewhere|
|fetch |diff adds cmake and utilizes FetchContent|

[^_l]: see [SPDX License List](https://spdx.org/licenses/ '') for a list of commonly found licenses
[^_d]: see table above with description of diff
