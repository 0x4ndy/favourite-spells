# AD

### PowerView - import PowerView (required before using PowerView functionalities)
```bash
Import-Module .\PowerView.ps1
```
---

### PowerView - list logged-in users
```bash
Get-NetLoggedon -ComputerName <computer_name>
```
---

### PowerView - list active sessions on a Domain Controller
```bash
Get-NetSession -ComputerName <computer_name>
```
---
