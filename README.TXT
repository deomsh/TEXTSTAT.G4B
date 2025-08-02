TEXTSTAT.G4B

Function: 
detect zeros before last EOL
count lines (with EOL & Text-type)
count labels
count remark(ed)-lines
returns line-number(s) with spaces at begin and/ or end-of-line
count chars of longest line
optional: export counts in variables (with switch)
optional: quited operation, export counts in variables only (with switch)
optional: count phrase (with switch)
optional: print lines containing counted phrases (with extra switch)
optional: quiet operation, export number of counted phrases as 'result' only (with extra switch)
optional: read text files - fully or a range (with extra switch)

Help     TEXTSTAT.G4B v0.8.1 (20250802), by deomsh (idea P-switch: steve6375)
Use      TEXTSTAT.G4B ["]FILE["] [switches]
Switches ["][/]COUNT[c]:phrase["] to count 'phrase', COUNTc: case-sensitive
         ["][/][N]A:phraseA["] [not] count if 'phrase' is just after phraseA
         [/]R[N]A:n [not] near-range for end of phraseA before 'phrase', n>=1
         [/]O[N]A:n offset between end of phraseA and begin of 'phrase', n>=1
         ["][/][N]B:phraseB["] [not] count if 'phrase' is just before phraseB
         [/]R[N]B:n [not] near-range for start of phraseB after 'phrase', n>=1
         [/]O[N]B:n offset between start of phraseB and end of 'phrase', n>=1
         [/]P to print counted 'phrase'-lines to screen (not with /Q)
         [/]R to read FILE. Screen not filled out, only full lines printed
         [/]R:s to start reading at line 's' (if 's' too high, last line only)
         [/]R:s-n or [/R]:s:n to read range: start line 's' - end line 'n'
         /V to get output in variables too
         /Q quiet operation, includes /V + [/]COUNT[c]:phrase 'result' only
         [/]MDBASE:startsector - >=0x3000 (default), max 4096 sectors used
Remarks  FILE must be a textfile, max 2097152 bytes (2 MB/ 4096 sectors)
         Switches are not case-sensitive and order is free (but after FILE)
         Switches /P and /R[:s[-|:n]] do not support mixed EndOfLine markers
         /R[:s[-|:n]] overrules /COUNT[c]:phrase and /P and sets /Q to /V
         'phrase' max 48 chars, use double-quotes IF containing spaces or '='
         For double-qoute use \x22,\ for '%' use \x25, for space \x20 if needed
         EndOfLine markers at begin OR end of 'phrase': \x0A, \x0D\x0A or \x0D
         For counting '\' use double '\\', count \xASCII: \\x.. or \x5C\x78..
         Vars: TSSIZE TSLINES TSTXTYPE TSLABELS TSHASH TS_HASH TS2COL TS_2COL
         TS_SCOL_ TSREM TS_REM_ TSBSPACE TSESPACE TSMAXLEN TSZEROS TSCOUNT
         Var 'result' only (same as TSCOUNT): ["][/]COUNT[i]:phrase["] /Q
Example  TEXTSTAT.G4B TEXTSTAT.G4B
Example  /TEXTSTAT.G4B /TEXTSTAT.G4B
Example  TEXTSTAT.G4B (fd0)/TEXTSTAT.G4B
Example  TEXTSTAT.G4B TEXTSTAT.G4B "/COUNT:if \x22"
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:\x0Aif /Q ;; set result
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:example
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNTc:example
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:\x25@retval\x25 /P
Example  TEXTSTAT.G4B TEXTSTAT.G4B "/COUNT:cat " "/NA:raw "
Example  TEXTSTAT.G4B TEXTSTAT.G4B "/COUNT:call " /NB:\x3A /P
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:cat /A:raw /OA:1 /P
Example  TEXTSTAT.G4B TEXTSTAT.G4B COUNT:\x3D\x25 A:set OA:12 B:\x25 RB:8 /P
Example  TEXTSTAT.G4B TEXTSTAT.G4B /R
Example  TEXTSTAT.G4B TEXTSTAT.G4B /R:144
Example  TEXTSTAT.G4B TEXTSTAT.G4B /R:543 /V ;; set TS
Example  TEXTSTAT.G4B TEXTSTAT.G4B /R:543-599
Example  TEXTSTAT.G4B TEXTSTAT.G4B /V ;; set TS
Example  TEXTSTAT.G4B TEXTSTAT.G4B /Q ;; set TS

Help     TEXTSTAT.G4B [/?]
         Prints lines above to screen: Help - (last) Example

BTW Written for grub4dos 0.4.6a (legacy), tested on grub4efi
If use with grub4efi gives problems, try graphics mode. Command: graphicsmode -1 640 (or -1 800 or -1 1024)
If graphics mode gives problems, try text mode. Command: graphicsmode 3

KNOWN BUGS (in latest version)
line-number(s) with spaces at end-of-line displayed ONE number too high in case of EOL's Unix/ Mac

History
v0.8.1
BUGFIX: switch ["][/]COUNT[c]:phrase["] always case-sensitive with / (in [/])

v0.8
Max file-size raised to 2 MB
If printing all counted phrases in smae line printed together
Conditional counting/ printing
Reading of text files, lines numbered
Possibility to start/ end reading at chosen line number(s)

v0.7.2
Interrupt [Hit Q...] is working to abort further printing to screen of lines containing counted 'phrase' and exit script
Highlighting of each 'phrase' inside lines printed to screen

v0.7.1
Correction of Examples in Help: FILE comes before switch(es)

v0.7
Count of lines starting with space
Added switch /V to export all counts as variables
Added switch /Q for quiet operation and export counts as variables
Added switch /P to print counted lines containing 'phrase' to screen 
Better handling of first line of text-files
Refuses FILE containing '%'
Switch /MDBASE:startsector exits if below 0x3000

v0.6.1
Switch /COUNT[C]:phrase supports graphicsmodes
Count of 'phrase' extended to 48 chars included counting \xASCII-codes with \x5C\x78code
Added Switch /MDBASE:startsector to set startsector for memory-use other than default

v0.6
Added count of 'phrase'

v0.4
First published version

BONUS

VERSION.G4B v0.1 (20221121), by deomsh
Function Display first line of text-file 'FILE' containing file-name
         Or display grub4dos version date
Use1     VERSION.G4B ["]FILE["]
Use2     VERSION.G4B grub4dos
Remark   Without device/ path: file-name is searched on ROOT ('/' not needed, except if file-name is 'grub4dos')

BONUS II

PAGESTAT.G4B v0.3 (20230120), by deomsh
Function Get GRUB4dos/efi and version
         Get graphicsmode
         Get number of chars on a line 
         Get number of lines on screen
         Get number of printable chars on one screen (without scrolling 1 less)
         Get length of tab (\t or '09')
         Get number of columns
Use      PAGESTAT.G4B [switch|/?]
Remarks  Switch /V stats exported as variables: GRUB GRUBVER GRPHMODE LINELEN PAGELEN TABLEN COLUMNS CHARS
         /Q same, but quiet operation
         /T to see output of Fn.4 (horizontal at column 0)
         /W test writing of all ASCII chars, one grey space after
         /W1 same, blank space before. /W2 as /W, highlight x after. /W3 as /W, blank space after

History:
v0.3
Bugfix number of columns
Better compatibility with grub4efi

v0.2
Added 'real' count of chars on page
Added count of tab length
Added count of columns
Added /V-switch
Added /T-switch
Added /W-switches
Added try GRUB4dos/efi + version

v0.1
First published version
