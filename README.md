# gw2-affinity
Launches Gw2-64.exe with thread affinity

Guild Wars 2, like most games, appears to run better when only using one logical core per physical core.
This program (once compiled) will execute the included batch file, and launch GW2-64.exe so that it only
uses cores 0, 2, 4, and 6. Since I designed this program for quad-core hyperthreaded processors, you will
need to modify Gw2-64-affinity.bat if you want to specify different cores. I've split the program into
two files so that users can specify which cores to use or which exe to launch without having to recompile
the program.

start /affinity 55 Gw2-64.exe -mapLoadInfo -autologin

exit

"/affinity 55" selects which cores to use. How? Each core is tied to one bit in what I'm presuming is a
one-byte value. You must convert these values (1, 2, 4, 8, 16, etc.) to hex, and then add them up.

Core 0 = 1

Core 1 = 2

Core 2 = 4

Core 3 = 8

Core 4 = 10

Core 5 = 20

Core 6 = 40

Core 7 = 80

It may be possible to go higher for 6 or 8-core processors, but I haven't tested it. Here are the numbers
you'll need for different CPUs:

Single-core:  1

Dual-core:    5

Quad-core:    55

"-mapLoadInfo" and "-autologin" are launch parameters that I like to use, feel free to remove them or add
your own. If you don't use the 64-bit beta (which you should), simply erase the "-64" from "Gw2-64.exe".

