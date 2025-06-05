- [ ] will implementation
  - [x] sub-packages
  - [x] run install scripts
  - [ ] run remove script?
  - [x] collection packages
  - [ ] alternative packages
  - [x] check install dependencies
  - [x] check execute dependencies
  - [ ] autocomplete script(s)
    - [ ] bash
    - [ ] zsh
  - [ ] load shim when needed?
  - [x] willup script (i.e. `wget <someurl> | sh` to install will)
  - [ ] commands that maintain the library collection
    - [x] stupid pkglib update
    - [ ] merging pkglib update
  - [ ] option to run up/down script files rather than pass packages on cmdline
  - [ ] a location for my own (md) documentation to go, and a `-e` flag to edit it
        (is there a tool I can use to browse md on the terminal rather than read it raw?)
  - [ ] cat logs

- [ ] specific packages
  - [x] bat-gadgets
  - [x] posix package(s)
    - [ ] perhaps recategorize according to https://en.wikipedia.org/wiki/List_of_Unix_commands
  - [ ] commonly-known util compilations
    - [ ] busybox
    - [ ] toybox https://en.wikipedia.org/wiki/Toybox
    - [ ] gnu coreutils https://en.wikipedia.org/wiki/List_of_GNU_Core_Utilities_commands
    - [ ] util-linux https://en.wikipedia.org/wiki/Util-linux
    - [ ] stuff required to build a linux kernel
  - [ ] csvkit
  - [ ] netstat, ss
  - [ ] script
  - [ ] yes, killall
  - [ ] system monitors (e.g. conky, but what others are available?)
  - [ ] "Android Device USB Connect"
  - [ ] color picker, in dotsync set a ctrl-alt keybinding
  - [ ] stuff from my system notes
  - [ ] any other common utilities?
  - [ ] "reversing" tools (file, objdump and the like)
  - [x] technicolor
  - [x] haskell
    - [x] ghc
    - [x] cabal
    - [x] env-cabal
    - [x] ghcup
      - [ ] ghc versions
      - [ ] cabal versions
      - [ ] hls versions
  - [ ] aspell
  - [ ] sqlitebrowser
  - [ ] desktop stuff
    - [ ] launcher (dmenu, rofi)
    - [ ] panel (polybar, xmobar)
  - [ ] cross-compilers, qemu, and so on
  - [x] ssh, sshd
  - [ ] user-land httpd (mini-httpd, droopy, ...?)
  - [ ] apparently xmenu is really good with a tiling window manager
  - [ ] plan9 from userspace?
- [ ] specific alt pkgs
  - [ ] dl: wget/curl/http one (or more?) files from the internet
  - [ ] syspkg: apt/pacman/whatever
- [ ] specific utilities
  - [ ] search and destroy: search for process by name, filter out the grep, and prompt for license to kill
  - [ ] search for SECRETS folders in home (or in `/`)
  - [ ] choose a basic encryption method
  - [ ] consider project startup scripts integrating my best practices
  - [ ] something that can try to find documentation for an arbitrary command (man page, --help, elsewhere)
  - [ ] `view` command to run `file` and determine the appropriate viewer (`less`, `vi -R` for syntax highlighting, binary explorers, image viewers,&c), `view -c` to run a command and pipe to `less -R`, but also figure out how to insert a `-C` or `--color` flag for the given command
    - I could just hardcode commands; it'll run all the rest of the arguments, but only after checking the first one to arrange some new flags and pipes
  - [ ] look at github releases to determine updates

- [ ] organize
  - [ ] split at least some stuff out of stdlib:
    - [ ] development environments
    - [ ] my user-y stuff
    - [ ] package managers

at some point, I'll likely move past plain utilities
  probly create basic directory structures
  maybe dotsync will be subsumed
  perhaps I'll need to pass arguments (e.g. which versions of ghc do I need?), or otherwise configure packages

I'll also need to manage when multiple library repos offer the same package
  probably just write repos in order, later repos override the packages of earlier repos


here's an idea:
```
ghc/
  alts = `ghc/8.10.2\nghc/8.10.4`
  check.sh
  8.10.2/
    check.sh = `exec ../check.sh 8.10.2`
  8.10.4/
    check.sh = `exec ../check.sh 8.10.4`
haskell/
  multi = `ghc\ncabal`
```
there's no problem using a slash in a module name

the thing is, I might actually want to allow for scan functionality to find these sub-packages
i.e. a package can include a list of more packages relative to itself
