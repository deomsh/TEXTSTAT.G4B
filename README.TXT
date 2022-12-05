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

Help     TEXTSTAT.G4B v0.7.2 (20221126), by deomsh (idea P-switch: steve6375)
Use      TEXTSTAT.G4B ["]FILE["] [switches]
Switches [/]COUNT:phrase or "[/]COUNT:phrase" to find count of 'phrase'
         [/]COUNTC:phrase or "/COUNTC:phrase" same, but case-sensitive
         [/]MDBASE:startsector - default 0x3000, max 511 sectors used
         /V to get output in variables too
         /Q quiet operation, includes /V
         ["][/]COUNT[c]:phrase["] to count 'phrase', COUNTc: case-sensitive
         /P to print counted 'phrase'-lines to screen (not mixed EOL's or /Q)
         [/]MDBASE:startsector - >=0x3000 (default), max 511 sectors used
Remarks  FILE must be a textfile, max 261632 bytes (255,5 KB/ 511 sectors)
         Switches are not case-sensitive and order is free (but after FILE)
         'phrase' max 48 chars, use double-quotes IF containing spaces or '='
         For double-qoute use \x22,\ for '%' use \x25, for space \x20 if needed
         EndOfLine markers at begin OR end of 'phrase': \x0A, \x0D\x0A or \x0D
         For counting '\' use double '\\', count \xASCII: \\x.. or \x5C\x78..
         Vars: TSSIZE TSLINES TSTXTYPE TSLABELS TSHASH TS_HASH TS2COL TS_2COL
         TS_SCOL_ TSREM TS_REM_ TSBSPACE TSESPACE TSMAXLEN TSZEROS TSCOUNT
         Var 'result' only (same as TSCOUNT): ["][/]COUNT[i]:phrase["] /Q
Example  TEXTSTAT.G4B TEXTSTAT.G4B
Example  (hd0,0)/TEXTSTAT.G4B (hd0,0)/TEXTSTAT.G4B /V ;; set TS
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:if
Example  TEXTSTAT.G4B TEXTSTAT.G4B "/COUNT:if not"
Example  TEXTSTAT.G4B TEXTSTAT.G4B "/COUNT:if \x22"
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:\x0Aif /Q ;; set result
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:example
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNTc:example
Example  TEXTSTAT.G4B TEXTSTAT.G4B /COUNT:\x25@retval\x25 /P
Example  TEXTSTAT.G4B TEXTSTAT.G4B COUNT:\x5C\\x7825@retval\\x5C\\x7825

Help     TEXTSTAT.G4B [/?]
         Prints lines above to screen: Help - (last) Example

BTW Written for grub4dos 0.4.6a (legacy), not tested on grub4efi.
If use with grub4efi gives problems, try graphics mode. Command: graphicsmode -1 640 (or -1 800 or -1 1024)
If graphics mode gives problems, try text mode. Command: graphicsmode 3

History
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

PAGESTAT.G4B v0.2 (20221204), by deomsh
Function Get GRUB4dos/efi and version
         Get graphicsmode
         Get number of chars on a line 
         Get number of lines on screen
         Get number of printable chars on one screen (without scrolling 1 less)
         Get length of tab (\\t or '09')
         Get number of columns
Use      PAGESTAT.G4B [switch|/?]
Remarks  Switch /V stats exported as variables: GRUB GRUBVER GRPHMODE LINELEN PAGELEN TABLEN COLUMNS CHARS
         /Q same, but quiet operation
         /T to see output of Fn.4 (horizontal at column 0)
         /W test writing of all ASCII chars, one grey space after
         /W1 same, blank space before. /W2 as /W, highlight x after. /W3 as /W, blank space after

History:
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
