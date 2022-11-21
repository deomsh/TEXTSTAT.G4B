# TEXTSTAT.G4B

TEXTSTAT.G4B v0.6.1 (20221021), by deomsh

Function: 
detect zeros before last EOL
count lines (with EOL & Text-type)
count labels
count remark(ed)-lines
returns line-number(s) with spaces at end-of-line
count chars of longest line
optional: count phrase with switch

Use 1 TEXTSTAT.G4B [switch] FILE
Use 2 TEXTSTAT.G4B [switch] "FILE"
Use 3 TEXTSTAT.G4B [/?]
Switches [/]COUNT:phrase or "[/]COUNT:phrase" to find count of 'phrase'
         [/]COUNTC:phrase or "/COUNTC:phrase" same, but case-sensitive
         [/]MDBASE:startsector - default 0x3000, max 511 sectors used
Remarks  FILE must be a textfile, max 261632 bytes (255,5KB)
         Switches are not case-sensitive
         'phrase' max 48 chars; if containing spaces or '=', use double-quotes
         For double-qoute char in 'phrase' use \x22, % in 'phrase' use \x25
         End Of Line markers at begin/ end of 'phrase': \x0A, \x0D\x0A or \x0D
         Counting \xASCII-codes: use \\x5C\\x78code (code is hex-number)
Example  TEXTSTAT.G4B TEXTSTAT.G4B
Example  /TEXTSTAT.G4B /TEXTSTAT.G4B
Example  (hd0,0)/TEXTSTAT.G4B (hd0,0)/TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:if TEXTSTAT.G4B
Example  TEXTSTAT.G4B "/COUNT:if not" TEXTSTAT.G4B
Example  TEXTSTAT.G4B "/COUNT:if \x22" TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:\x0Aif TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:example TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNTC:example TEXTSTAT.G4B
Example  TEXTSTAT.G4B /COUNT:\x25@retval\x25 TEXTSTAT.G4B
Example  TEXTSTAT.G4B COUNT:\\x5C\\x7825@retval\\x5C\\x7825 TEXTSTAT.G4B

History
v0.6.1
Switch /COUNT[C]:phrase supports graphicsmodes
Count of 'phrase' extended to 48 chars included counting \xASCII-codes with \\x5C\\x78code
Added Switch /MDBASE:startsector to set startsector for memory-use other than default

v0.6
Added count of 'phrase'

v0.4
First published version
