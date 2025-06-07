# dwmblocks
Modular status bar for dwm written in c.
# usage
To use dwmblocks first run 'make' and then install it with 'sudo make install'.
After that you can put dwmblocks in your xinitrc or other startup script to have it start with dwm.
# how is this different?
## fixed termhandler signature
`termhandler`s fixed according to the correct (`void handler(int)`) signature of handlers (which threw a compile error).

## builtin statuscmd
the statuscmd patch diff file needed a little bit of tinkering to be added to
the newest dwmblock source code. the tinkering is done, and instead of a patch
its built into it

## multi-threaded signal handling
because of the single threaded nature of dwmblocks, executing multiple commands
at once (multiple signals, and the intervaled commands) made one or more of the
block executions fail, and it had no output till the next interval (if this
issue wasn't persistent then too). this is fixed using a pthread multi-threaded
signal handling approach.

# modifying blocks
The statusbar is made from text output from commandline programs.
Blocks are added and removed by editing the blocks.h header file.
By default the blocks.h header file is created the first time you run make which copies the default config from blocks.def.h.
This is so you can edit your status bar commands and they will not get overwritten in a future update.
