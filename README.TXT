# TEXTSTAT.G4B

TEXTSTAT.G4B v0.6 (20221017), by deomsh

Function: 
count zeros before last EOL
count lines (with EOL & Text-type)
count labels
count remark(ed)-lines
returns line-number(s) with spaces at end-of-line
count chars of longest line
optional: count phrase with switch

Use 1 TEXTSTAT.G4B [switch] FILE
Use 2 TEXTSTAT.G4B [switch] "FILE"
Use 3 TEXTSTAT.G4B [/?]
Switches /COUNT:phrase or "/COUNT:phrase" to find count of 'phrase'
         /COUNTC:phrase or "/COUNTC:phrase" same, but case-sensitive
Remarks  FILE must be a textfile, max 261632 bytes (255,5KB)
         Switches are not case-sensitive
         'phrase' max 16 chars; if containing spaces, use double-quotes
         For double-qoute char in 'phrase' use \x22
         End Of Line markers at begin/ end of 'phrase': \x0A, \x0D\x0A or \x0D
         For % in 'phrase' use \x25 (if needed)
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


