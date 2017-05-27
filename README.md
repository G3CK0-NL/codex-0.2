# codex-0.2
The swiss army knife for hackers

Thank you for using the Codex - the swiss army knife for hackers.

Disclaimer: This is a beta version. A lot of functionality is not there yet. If you find bugs in the working stuff, please mail me: [G3CK0@G3CK0.nl](mailto:G3CK0@G3CK0.nl).

# Requirements
This tool requires **Java SE Runtime Environment (JRE) version 7**.
The tool runs on all platforms having the above Java version (or newer).

**Debian/Ubuntu/Kali users**
```sh
$ sudo apt-get install openjdk-8-jre
```

**Windows users**

[Get JRE v7 (or newer) from the java.com website](http://www.oracle.com/technetwork/java/javase/downloads/).

# Installation
No installation is needed (this is a portable tool). Just download the zip:
```sh
$ wget https://github.com/G3CK0-NL/codex-0.2/archive/master.zip
```
Or use git:
```sh
$ git clone https://github.com/G3CK0-NL/codex-0.2.git
```
Be sure to verify the integrity of the jar using a sha sum:
```sh
sha512: d4e3c27b93f4f9fc79b507b4ed5aab7026839de09f94f70186b7de088656dc9e19c3b9b180035c81b1fd83177fd204fe86e27a41f9432d3ef8533d835c0c42d2
sha256: 06a9f9e298998becb643ece153425d101d01ae7dd58a90751b47d5d843a9ecc3
sha1:   c6edf4c1b8621f975e3efeaa17590f062a36327c
```

# Usage
Start through GUI: Doubleclick!
Start through CLI: 
```sh
$ java -jar codex.jar
```

Examples to send text/data to the tool through the CLI:
```sh
$ cat /etc/passwd | java -jar codex.jar
$ java -jar codex.jar /etc/passwd
$ java -jar codex.jar < /etc/passwd
```
You can also send the generated result/output of the tool (right pane) to stdout. This enables command-line passing, for example:
```sh
$ cat /etc/passwd | java -jar codex.jar > somedumpfile.txt
$ cat /etc/passwd | java -jar codex.jar | sort -u | head
```
# Copyright © 2015, G3CK0
Permission to use, copy, and/or distribute this software for any purpose without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.  THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING BUT NOT LIMITED TO ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY DIRECT, INDIRECT, CONSEQUENTIAL OR SPECIAL DAMAGES OR ANY OTHER DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING FROM, OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.  

# Changes in version 0.2 
## New functionality
The following functionality is added in this version: 
- Added the following new conversions:
    - Gray code
    - Morse
    - Unicode (2 byte) text strings (encoding only, for now)
- Added the following new encryptions:
    - Atbash (rot-0 reversed alphabet) quick setting in rot encryption tab
- Added the "Text" tab. The codex is now packing a complete array of text manipulation options:
    - Search - Grep through text
    - Replace - Replace text with different text
    - Extract - Extract a substring from a string. This can be done in multiple ways:
        - By column (using some seperator and a column number)
        - By two separators
        - By character index (start/end/length)
    - Sort - Sort lines of text (or words) alphabetically. You can also sort unique occurrences (and obtain the counts).
    - Delimiter - This transcoder makes it possible to add, change and remove text delimiters (for example in CSV formats).
    - Multiple utilities:
        - Make uppercase or lowercase
        - Reverse text
        - Delete empty lines
        - Trim text
        - Modify newlines (DOS vs Linux vs none)
- Added the "Web" tab. This adds the following functionality: 
    - URLencoding and -decoding (replaces characters like & ? + and space)
    - To/from HTML characters (replaces characters with their &#..; equivalent)
    - Encode string to javascript fromCharCode() function
    - Strip XML/HTML tags
- Added the "Generate" tab. You can now generate: 
    - Ranges of numbers
    - Random numbers
    - Ranges of characters (by ASCII value)
    - Random characters (based on candidate text)
    - Text based on custom text (create NOP-sleds, etc)
    - Lorem Ipsum placeholder text
- Added the following interactive listings and tools to the upper toolbar: 
    - ASCII table. Table is searchable and copies values to clipboard on doubleclick and right mouse click
    - Network port list. This list contains over 9000 ports, listing both formal and malware use (based on SANS lising)
    - Well-known extension list
    - MAC address vendor list
    - Color chooser

## New application features
The following application features are added in this version:
- Add line numbers to the text areas
- Added zooming capability (Ctrl-scroll / Ctrl + / Ctrl - / Ctrl 0) to the text areas.
- You can now pipe data to the application like:
    cat /etc/passwd | java -jar codex.jar
- You can input data to the application like:
    java -jar codex.jar < /etc/passwd
- Clear function added to toolbar.
- Upon exit (with data in output screen) the save options are changed: "output to stderr" is replaced with "output to clipboard".
- Option "paste over all" added to textfield context menu.
- Added application icon ;)
- Added tooltips in: mainframe, panels: convert, encoding-base, encoding-uu, hash, generate, crypt-rot, crypt-xor, text-search, text-replace, text-extract, text-sort, text-delimiter.
- Moved word-wrap option to context menu.
- Added about box, containing lots of information about the tool.
- Added context menu for accessing the about box and changing loglevels.

## Bugfixes
The following bugs are fixed in this version: 
- Converter > From Hex: selecting a period as seperator results in an empty output, instead of correctly decoded output.
- Toolbar can be dragged off the form.
- Piping data to application doesnt work.
- Piped data does not automatically fire selected transcoder and update output text window.
- Multi-line input results in output with an empty last line.
- Encoding > base: 'Like hex' checkbox does not work (disabled, awaiting creation of base64 implementation selector).
- Encoding > base: exception was thrown when certain illegal base64 lines where entered.
- Hard to see that textboxes are disabled. Background color should change.
- PrefixPostfixSeperator > could not handle absent seperator & present prefix/postfix. Now splitting on prefix/postfix if seperator is not there.
- First transcoder (convert) not selected on keep and clear.
- Changed font to a monospaced one. This improves readability and usability.
- Newline type was empty by default, and newline type detection does not run in corner cases (eg when using the generate transcoder).
- Newline type detection did not function properly: when the amount of DOS and Linux newlines is equal, we have DOS newlines, as the Linux newline is a subset of a DOS newline.
- Text on uuEncode and yEncode panel was not visible.
- Clipboard integration didn't work under OpenJDK.
- Zooming: needed to select input text panel to make ctrl+scroll work.
- Pressing ALT-F4 fires exit procedure twice.
- Pressing ESC when in a close window exits the complete application, but should cancel the window.
- When pressing ALT-F4, repeatedly pressing F4 results in piles of exit calls.
- Pressing ESC in tool windows will terminate the complete application.
- In text -> utilities -> newline replacement, you could only replace and delete newlines if you where not in line mode.
- Entering illegal hex values in XOR crypt key field resulted in a NumberFormatException. This is now handled correctly.
- XOR crypting did not work correctly in line mode, as the encrypted data can contain newlines. Changed to raw transcoder.
- File save: saving result text did not actually save the text.

## Technical improvements
The following technical improvements are made in this version: 
- Surrounded transcoder calls with try-except to prevent application failure on transcoder failure.
- Extracted the two main text panes to seperate files, to enable the possibility of multiple views in the future.
- Interactive ASCII table is split into the table popup and an ASCII data populator. This will speed up implementation of different tables.
- Replaced AdvancedTranscoder to RawTranscoder, where the RawTranscoder receives the complete original text, allowing transcoders to work in one go. Three transcoders currently use this: Generator (to generate once, instead of every line), Sorter (to sort everything) and Utilities (to replace newlines).

## Known bugs
- Not yet implemented: 
    - Encoding > uuEncode
    - Encoding > yEncode
    - Crypto > AES
    - Crypto > Vignere
    - Crypto > Enigma
    - Text > count
    - Text > Extract > Column and Seperator: inverse selection
- Known bugs (tolerated & ignored for now!) 
    - Need to click outside of spinners for change to take effect.
    - Type text, try to exit, press red cross or ALT-F4 to cancel exit from save dialog, after this, the first following escape will be ignored.
    - Unicode text to text decoding cannot be implemented correctly because source data to converter is supplied by string. This messes with the unicode data.
    - Unicode encoding scheme (big- or little endian) detection is done in a crappy way right now. Waiting for settings function?!
    - XOR decrypting ignores/overrides line-mode setting. This is because XOR-encrypted data can/will contain newlines.
    - The hex view is not functioning yet, working on it... Disabled for now
    - Column extractor: empty columns (returned as "") are completely ignored by controller (like null result).
    - uuEncoding: The encoding is not working (error in cryptex lib)
