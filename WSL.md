# Instalace Windows Subsystem for Linux
Postup zkoušen na Windows 10 Home (2004)

## Instalace WSL
Následující postup je prováděn v Příkazovém řádku systému Windows. Může být nutný administrátorský přístup.
1. `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`
1. `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`
1. Restartujte zařízení.
1. Stáhněte aktualizaci WSL2 z [core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) (oficiální web Microsoftu).
1. Projděte instalačním dialogem a aktualizaci nainstalujte.
1. `wsl --set-default-version 2`
1. Přejděte do obchodu Microsoft Store a nalezněte vhodný Linux (Debian, Ubuntu, Alpine, ...)
1. Získejte a nainstalujte vybraný Linux.
1. Po dokončení instalace ho spusťte a nastavte administrátora.

## Potíže v Debianu
### Žádné připojení k internetu
1. V Debianu: `nano /etc/wsl.conf`
1. Do souboru zadejte:
`[network]
generateResolvConf = false`
1. V cmd.exe ve Windows: `wsl --shutdown`
1. V cmd.exe ve Windows: `wsl`
1. V Debianu: `sudo -i`
1. V Debianu: `nano /etc/resolv.conf`
1. Opravte nameserver, např. `nameserver 8.8.8.8` (Google DNS)
