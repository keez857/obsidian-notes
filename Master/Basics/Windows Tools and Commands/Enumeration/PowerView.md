### PowerView cheatsheat
https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993

Start Powershell
`powershell -ep bypass`

Start PowerView
`. .\Downloads\PowerView.ps1`

Enumerate domain users
`Get-NetUser | select cn`

Enumerate domain groups
`Get-NetGroup -GroupName *admin*`

Find network shares
`Invoke-ShareFinder`

List OS
`Get-NetComputer -fulldata | select operatingsystem`