TEXTSTAT.G4B v0.7 (20221122), by deomsh

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

Use TEXTSTAT.G4B ["]FILE["] [switches]
Switches [/]COUNT:phrase or "[/]COUNT:phrase" to find count of 'phrase'
         [/]COUNTC:phrase or "/COUNTC:phrase" same, but case-sensitive
         [/]MDBASE:startsector - default 0x3000, max 511 sectors used
         /V to get output in variables too
         /Q quiet operation, includes /V
         ["][/]COUNT[i]:phrase["] to count 'phrase', COUNTi: case-sensitive
         /P to print counted 'phrase'-lines to screen (not mixed EOL's or /Q)
         [/]MDBASE:startsector - >=0x3000 (default), max 511 sectors used
Remarks  FILE must be a textfile, max 261632 bytes (255,5 KB/ 511 sectors)
         Switches are not case-sensitive and order is free (but after FILE)
         'phrase' max 48 chars, use double-quotes IF containing spaces or '='
         For double-qoute use \x22,\ for '%' use \x25, for space \x20 if needed
         EndOfLine markers at begin OR end of 'phrase': \x0A, \x0D\x0A or \x0D
         For counting '\' use double '\\', count \xASCII: \\x.. or \x5C\x78..
         Output: max TSLINES TSTXTYPE TSLABELS TSHASH TS_HASH TS2COL TS_2COL
         TS_SCOL_ TSREM TS_REM_ TSBSPACE TSESPACE TSMAXLEN TSZEROS TSCOUNT
         Output 'result' (value as TSCOUNT): ["][/]COUNT[i]:phrase["] /Q
Example  TEXTSTAT.G4B TEXTSTAT.G4B
Example  (hd0,0)/TEXTSTAT.G4B (hd0,0)/TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:if TEXTSTAT.G4B
Example  TEXTSTAT.G4B "/COUNT:if not" TEXTSTAT.G4B
Example  TEXTSTAT.G4B "/COUNT:if \x22" TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:\x0Aif TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:example TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNTC:example TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:\x25@retval\x25 TEXTSTAT.G4B
Example  TEXTSTAT.G4B COUNT:\\x5C\\x7825@retval\\x5C\\x7825 TEXTSTAT.G4B

Help     TEXTSTAT.G4B [/?]
         Prints lines above to screen

History
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
Remark   Without device/ path: file-name is searched on ROOT ('/' not needed)
