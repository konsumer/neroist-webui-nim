# WebUI

> *Use any web browser as GUI, with Nim in the backend, and*
> *HTML/Nim/JS/TS/CSS in the frontend.*

![Image](https://raw.githubusercontent.com/malisipi/vwebui/main/screenshot.png)

Nim wrapper and bindings for [WebUI](https://github.com/alifcommunity/webui), a
fully independent and cross-platform web UI library.

Instead of using a third-party library, WebUI instead uses a pre-installed
browser (Edge, Firefox, Chrome, Chromium, or Safari). So, there's no need for any
large SDK or library for development/production, all you need is a web browser!

> :warning: **Notice**:
>
> * WebUI is not a web-server solution or a framework, but it's an easy-embeddable
> tool to use any installed web browser as a user interface.
>
> * WebUI's documentation is **not** finished.
>
> * WebUI is not ready yet for production release.

## Features

* Fully Independent (*No need for any third-party library*)
* Lightweight (*~600 Kb* (*300 Kb when compiling with DLL*)) & Small memory footprint
* Fast WS binary communication (*App--WebUI--Browser*)
* Multi-platform & Multi-Browser
* Uses private profile for safety

## Installation

Install via Nimble:

```shell
nimble install webui
```

## Documentation

Online documentation can be found here: 
  - <https://neroist.github.io/webui>
  - <https://neroist.github.io/webui-nimib-experimental-docs>

There isn't much documentation as of right now, so I suggest to get started
using some [examples](#examples) or WebUI's own
[examples](https://github.com/alifcommunity/webui/tree/main/examples) or
[documentation](https://webui.me/docs/).

Heres a very [*minimal*](examples/minimal.nim) example of using the wrapper:

```nim
import webui

let window = newWindow() # Create a new Window
window.show("<html>Hello</html>") # Show the window with html content

wait() # Wait until the window gets closed
```

### Examples

Examples can be found here at [`examples/`](examples/).

If you're trying to run the examples remember to clone the repository
*recursively*, as it depends on the WebUI repo as a submodule. Here's
the command to do so for the truly lazy:

```shell
git clone --recursive https://github.com/neroist/webui.git
```

## Bindings and Wrapper

The Nim library exposes two files: `webui.nim` and `webui/bindings.nim`.
`webui/bindings.nim` are low-level bindings for WebUI, generated by
[c2nim](https://github.com/nim-lang/c2nim). `webui.nim` is a high-level wrapper for
WebUI, using native Nim types and avoiding pointers.

The wrapper and bindings also allow to to control whether or not to statically
compile WebUI's C sources into your application, compile with a static library, or
to depend on a DLL. Static compilation is the default behavior.

To compile with a static library, pass `-d:useWebviewStaticLib` or
`-d:useWebviewStaticLibrary` to the Nim compiler. To depend on a DLL, pass
`-d:useWebviewDll` instead. If neither of these flags are passed to the Nim
compiler, static compilation will take place instead. Static libraries and DLLs can
be found in WebUI's website [here](https://webui.me/#download).

In addition, you can also enable WebUI's logging via `-d:webuiLog` but that flag
only works for static compilation.

## Supported Browsers

| OS      | Browser | Status        |
| ------  | ------  | ------        |
| Windows | Firefox | ✔️            |
| Windows | Chrome  | ✔️            |
| Windows | Edge    | ✔️            |
| Linux   | Firefox | ✔️            |
| Linux   | Chrome  | ✔️            |
| macOS   | Firefox | *coming soon* |
| macOS   | Chrome  | *coming soon* |
| macOS   | Safari  | *coming soon* |

## License

MIT License. See [LICENSE](LICENSE)

Original WebUI library is licensed under LGPL-2.1. See
[LICENSE](https://github.com/alifcommunity/webui/blob/main/LICENSE).
