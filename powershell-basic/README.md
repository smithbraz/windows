PowerShell

Get-Command 

Get-Command -CommandType "Function"

Get-Help Get-Date

Get-Alias

Get-ChildItem

Set-Location -Path "c:\users\"

New-Item -Path ".\folder\folder" -ItemType "Directory"

New-Item -Path ".\folder\folder\teste.txt" -ItemType "File"

Remove-Item -Path ".\folder\folder"

Remove-Item -Path ".\folder\folder\teste.txt"

Copy-Item -Path .\folder\folder\teste.txt -Destination .\folder\folder\teste1.txt

Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"

Get-ChildItem | Where-Object -Property "Name" -like "new*"

Get-ChildItem | Sort-Object Length

Get-ComputerInfo

(Get-ComputerInfo).BiosSeralNumber

(Get-ComputerInfo).OsName

(Get-ComputerInfo).OsRegisteredUser

Get-LocalUser

Get-LocalUser | Where-Object -Property "Enabled" -like "True"

Get-LocalUser | Where-Object -Property "Enabled" -like "False"

Get-LocalUser -Name "smith"

Get-LocalGroup

Get-LocalGroupMember -Name Administradores

Get-LocalUser -name smith | Format-List

Get-LocalUser -name smith | Select-Object FullName, Enabled, Name, SID

Get-NetIPConfiguration

Get-NetIPAddress

Get-NetTCPConnection

Get-Process

Get-Service

Get-Service | findstr Running

Get-FileHash -Path .\new.txt


# Aviso de Isenção de Responsabilidade – Material de Red Team
Este material destina-se exclusivamente a fins educacionais, acadêmicos e de conscientização em segurança da informação. As técnicas, exemplos e cenários aqui descritos têm como objetivo demonstrar vulnerabilidades potenciais e auxiliar profissionais de segurança na prevenção, detecção e resposta a ameaças.
• Não é permitido utilizar este conteúdo para atividades ilegais, maliciosas ou que violem políticas corporativas, regulamentos ou legislações vigentes.
• O uso indevido das informações apresentadas pode resultar em sanções legais, disciplinares e criminais.
• Os autores e distribuidores deste material não se responsabilizam por qualquer dano, perda ou consequência decorrente da aplicação inadequada ou não autorizada das técnicas descritas.
• Recomenda-se que qualquer prática de red team seja realizada em ambientes controlados, autorizados e com consentimento explícito das partes envolvidas.
