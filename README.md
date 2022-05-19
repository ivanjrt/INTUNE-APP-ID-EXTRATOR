# INTUNE-APP-ID-EXTRATOR
``` Ruby
Add-Type -AssemblyName Microsoft.VisualBasic
$appleID = [Microsoft.VisualBasic.Interaction]::InputBox('Catalog:
    https://www.apple.com/app-store/', 'Apple ID Finder:', "Please Input just Apple ID #")
 
$iTunesUrl    = "https://itunes.apple.com/lookup?id="
$appExtration = Invoke-RestMethod -Uri "$iTunesUrl + $appleID" -Method Get
$appExtration.results

Write-Host " "
Write-Host " "
Write-Host " "
Write-Host 'Your AppleID for: ' $appExtration.results.trackCensoredName 'is: '  $appExtration.results.bundleId -ForegroundColor Green
```
