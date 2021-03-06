# Scheme standards

Discussion R5RS, R6RS, R7RS, which one to target in what circumstances, and what kinds of problems to expect with each one.

Mention IEEE Scheme in passing, since people who are interested in standards may wonder about it.

# SRFIs by popularity, which are the usual ones for common tasks

*The popularity list could be automatically extracted from package/library metadata -weinholt*

# How to choose an implementation

## If you need to embed Scheme in a lower-level language

If you need to embed Scheme in a C/C++/Rust/Go application, natural choices are...

*C and C++: GNU Guile, Chibi Scheme, TinyScheme, Bigloo, Chez Scheme. Go: https://github.com/weinholt/conscheme (needs some work to be useful) -weinholt*

## If you need a Scheme for one of the big VM platforms

JVM, .NET CLR, JavaScript, WebAssembly/Asm.js

*JVM: Kawa. .NET: IronScheme or https://github.com/Microsoft/schemy. WebAssembly: https://github.com/google/schism -weinholt*

## If you need a Scheme for fast native applications

If you need fast native code, your options are pretty much... You will be limited to the these computer architectures: Intel; ARM/PPC?

*Chez Scheme supports i386, amd64, armhf and ppc32 (but currently only with 4K-page machines). The armhf build runs on arm64 machines that support 32-bit code, like the Raspberry Pi 3. -weinholt*

All Schemes have a fast startup time, or do they?

*Not really, it varies a lot. -weinholt*

## If you need Scheme to learn about programming

Most compatible Scheme to work through SICP, How to Design Programs, ...

*Definitely Racket for SICP -weinholt*

Racket with its GUI as a first programming language?

## If you need a Scheme for a niche application

Embedded systems

*Microscheme for Atmel processors https://github.com/ryansuchocki/microscheme and Armpit Scheme for ARM http://armpit.sourceforge.net/ (more useful links at the bottom of the page) -weinholt*

Scheme in Common Lisp, Ocaml, ...

## How many libraries are available for each Scheme

*R6RS implementations have https://akkuscm.org/packages/, which also has support for R7RS, and R7RS implementations have http://snow-fort.org/. Chicken has http://wiki.call-cc.org/chicken-projects/egg-index-5.html and Racket has https://pkgs.racket-lang.org/. Guile has some packages in Linux distributions and more in Guix. Akku can work with Guile modules, so there are a few there as well (should be more). -weinholt*

## How big the community is for each Scheme? Oriented to beginners/experts?

# Common portability pitfalls

## Text vs raw bytes; character encodings

*R6RS distinguishes between textual ports and binary ports. A binary port can be turned into a textual port through transcoding. There is a clear distinction between bytevectors and strings, just like in Python 3.x. -weinholt*

## Terminals, ANSI color, resize events, etc.

*For terminals there is the option of using an ncurses or termbox FFI wrapper. You can also have a look at https://gitlab.com/weinholt/text-mode where the meat of the code is in pure R6RS (FFI just for some syscalls). If you just want ANSI colors then Alex Shinn's fmt package is really nice. -weinholt*

## File system / Networking / OS interface

*Some have it built-in, like Racket and Guile. For Chez have a look at Swish that solves this and more https://github.com/becls/swish/. Unfortunately none of these result in portable code. -weinholt*

## GUI libraries