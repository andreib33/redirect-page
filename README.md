# Define the share location and output file
$sharePath = "\\aganfs"
$outputFile = "C:\Temp\credentials_found.txt"

# Keywords to search for
$keywords = "password", "user", "username", "credentials", "key", "secret"

# Search all file types (txt, cfg, ini, json, etc.)
Get-ChildItem -Path $sharePath -Recurse -Include *.txt, *.cfg, *.ini, *.json, *.log, *.xml | ForEach-Object {
    Select-String -Path $_.FullName -Pattern ($keywords -join "|") -CaseSensitive
} | Out-File -FilePath $outputFile -Encoding UTF8

Write-Output "Search complete. Results saved to $outputFile"
