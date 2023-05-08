MOTIONS:

- `w` to move word by word
- `b` to move backwards word by word
- `W` to move word by WORD
- `B` to move backwards WORD by WORD
- `E` is like `e` but operates on WORDS
- `gE` is like `ge` but operates on WORDS
- `O` open a line above current line and go to insert mode

- Use `f{character}` (find) to move to the next occurrence of a character in a line.
- Use `F{character}` to find the previous occurrence of a character
- Use `t{character}` to move the cursor just before the next occurrence of a character (think of `t{character}` of moving your cursor until that character).
- Again, you can use `T{character}` to do the same as `t{character}` but backwards
- to move to the next or previous occurrence, use `;` or `,`

- `0`: Moves to the first character of a line
- `^`: Moves to the first non-blank character of a line
- `$`: Moves to the end of a line
- `g_`: Moves to the non-blank character at the end of a line

- `}` jumps entire paragraphs downwards
- `{` similarly but upwards
- `CTRL-D` lets you move down half a page by scrolling the page
- `CTRL-U` lets you move up half a page also by scrolling

- `/{pattern}` to search forward - can be a regex!
- `?{pattern}` to search backwards
- `n` to go to the next match
- `N` to go to the previous match

- Use `gd` to **g**o to **d**efinition of whatever is under your cursor.
- Use `gf` to **g**o to a **f**ile in an import.

- Use `gj` to go down one WRAPPED line.
- Use `gk` to go up one WRAPPED line.

- Type `gg` to go to the top of the file.
- Use `{line}gg` to go to a specific line.
- Use `G` to go to the end of the file.
- Type `%` jump to matching `({[]})`.

EDITING:

- type `d` to delete with another operator like `w`: `dw` `4dw`.
- `u` undo
- `ctrl-r` redo
- delete from cursor until {x}: `dt{x}`, e.g @---fuck--- `ffdt-`
- `dd` will delete the entire line; doubling may work on other operators too.
- `D` removes everything from cursor to end of line, equivalent to d$
- `d/{x}` delete until {x}
- `c` operates like a combined `d + i`.
- `cf{x}` like `ct{x}` except it includes the search character, so 1 index different.

- Text objects can be words, sentences, quoted text, paragraphs, blocks, HTML tags, etc.
- w - word
- s - sentence
- p - paragraph
- ", ', ` - quotes (this one is special! the cursor doesnt have to be within the quotes, can before it.)
- `ci`: change inner
- `ca`: change around (includes delimiters)

- `y` (yank): Copy in Vim jargon
- `yy`: copy entire line
- `p` (put): Paste in Vim jargon
- `g~` (switch case): Changes letters from lowercase to uppercase and back. Alternatively, use `gu` to make something lowercase and `gU` to make something uppercase
- `>` (shift right): Adds indentation
- `<` (shift left): Removes indentation
- `=` (format code): Formats code

- `yiw` yanks the entire word under the cursor
- `viwp` replaces the word under the cursor with the yanked word (only seems to work once though)
  Another pattern might be:
  `yiw` => move to target word => `ciw` => `ctrl-r` => `0`; after that repeat with `.`

- `V%y` => when cursor is on opening bracket of func body, copies the entire function

`y` and `p` is how you copy and paste things in Vim. Like `d` and `c`, `y` can be combined with motions and text objects to copy any text that you desire:

- `x` is equivalent to `dl` and deletes the character under the cursor
- `X` is equivalent to `dh` and deletes the character before the cursor
- `s` is equivalent to `ch`, deletes the character under the cursor and puts you into Insert mode
- `r` allows you to replace one single character for another. Very handy to fix typos.
- `~` to switch case for a single character

- `i` lets you *i*nsert text before the cursor
- `a` lets you *a*ppend text after the cursor
- `I` lets you *i*nsert text at the beginning of a line
- `A` lets you *a*ppend text at the end of a line
- `o` lets you *o*pen a new line below the current line
- `O` lets you *o*pen a new line above the current line
- `gi` puts your cursor in insert mode the last place you made a change.

Removing text in Insert mode:

- `CTRL-H` lets you remove the last character you typed (mnemonic _h_ which in _hjkl_ brings the cursor one space to the left)
- `CTRL-W` lets you remove the last word you typed (mnemonic *w*ord)
- `CTRL-U` lets you remove the last line you typed (mnemonic *u*ndo this line)

Selecting Text:

- `v` for character-wise visual mode
- `V` for line-wise visual mode
- `C-V` for block-wise visual mode
- In visual line mode, use `o` to move the cursor back and forth from top/bottom of selection

- `ya[bracket]` copy everything in a bracket inc bracket
- `yi[bracket]` copy everything in a bracket exc bracket
- `di[bracket]` delete everyting in a bracket exc bracket
- `v%` when cursor is on the opening bracket, highlight everything inc bracket
- `vi%` when cursor is on opening bracket, highligth everything exc bracket
- `viw` select the current word only, without delimiters including whitespace
- `vw` select current word including delimiters & whitespace
- `v$` select from current position to end of line
- `D` removes everything from current character to end of line

Surrounds:
Surround text with brackets, parens, etc with `S`

- `S"` will surround highlighted text with double quotes - visual mode
- `S{` will surround highlighted text with curly braces - visual mode
- `ds[bracket, parens, etc]` will delete the bracket surrounding the current text
- `cs[old][new]` will replace the old surrounding with the new
- `ys[motion, e.g. "iw"][bracket]` will add brackets to the selection - normal mode

Multi-cursor:

- `gb` when the cursor is on a word, add multiple cursors on subsequent occurences
  At this point the words are highlighted in visual mode. Use any visual commands.
- `[esc]` will put the cursors into normal mode. Use any normal mode commands.

Moving the line:

- `zt` moves the current line to the top of the screen
- `zz` moves the current line to the middle of the screen
- `zb` moves the current line to the bottom of the screen

Moving the cursor:

- `H` moves cursor to top of the screen.
- `M` moves cursor to middle of the screen.
- `B` moves cursor to bottom of the screen.
