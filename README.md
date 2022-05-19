# APPLE APP ID EXTRATOR
``` Ruby
Add-Type -AssemblyName Microsoft.VisualBasic
$appleIdRaw = [Microsoft.VisualBasic.Interaction]::InputBox('Catalog:
    https://www.apple.com/app-store/', 'Apple ID Finder:', "Input full link for the Apple ID")
 
$iTunesUrl    = "https://itunes.apple.com/lookup?id="
$appleID      = $appleIdRaw -replace "\D+"

Try {
    $appExtration = Invoke-RestMethod -Uri "$iTunesUrl + $appleID" -Method Get
    clear
    Write-Host " "
    Write-Host " "
    Write-Host "checking..."
    sleep -Seconds 2 ; clear
    Write-Host 'Your AppleID for - ' $appExtration.results.trackCensoredName '- is: ' -ForegroundColor Gray
    Write-Host $appExtration.results.bundleId -ForegroundColor Green
    Write-Host " "
    Write-Host " "
    Write-Host " "
} Catch {
    clear
    Write-Warning "Your ID was not found. Please check again"
    Write-Warning "Are you Online or blocked by the Firewall or Internet Filter?"
}
```
