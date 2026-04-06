# PowerShell Commands

## Basic Commands

### Lista todos os comandos disponíveis no PowerShell.
```
Get-Command 
```
### Lista apenas funções internas do PowerShell.
```
Get-Command -CommandType "Function"
```
### Exibe ajuda/documentação sobre o comando Get-Date
```
Get-Help Get-Date
```
### Mostra os atalhos (aliases) de comandos.
```
Get-Alias
```
### Lista arquivos e pastas do diretório atual.
```
Get-ChildItem
```
### Muda o diretório de trabalho para "c:\users\"
```
Set-Location -Path "c:\users\"
```
### Cria uma nova pasta.
```
New-Item -Path ".\folder\folder" -ItemType "Directory"
```
### Cria um novo arquivo.
```
New-Item -Path ".\folder\folder\teste.txt" -ItemType "File"
```
### Exclui a pasta especificada
```
Remove-Item -Path ".\folder\folder"
```
### Exclui o arquivo especificado
```
Remove-Item -Path ".\folder\folder\teste.txt"
```
### Copia o arquivo para outro nome/local.
```
Copy-Item -Path .\folder\folder\teste.txt -Destination .\folder\folder\teste1.txt
```
### Filtra apenas arquivos .txt
```
Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"
```
### Filtra arquivos cujo nome começa com "new".
```
Get-ChildItem | Where-Object -Property "Name" -like "new*"
```
### Lista arquivos ordenados pelo tamanho
```
Get-ChildItem | Sort-Object Length
```
### Exibe informações detalhadas do computador
```
Get-ComputerInfo
```
### Mostra o número de série do BIOS
```
(Get-ComputerInfo).BiosSeralNumber
```
### Mostra o nome do sistema operacional
```
(Get-ComputerInfo).OsName
```
### Mostra o usuário registrado do sistema
```
(Get-ComputerInfo).OsRegisteredUser
```
### Lista usuários locais do sistema
```
Get-LocalUser
```
### Filtra usuários locais habilitados
```
Get-LocalUser | Where-Object -Property "Enabled" -like "True"
```
### Filtra usuários locais desabilitados
```
Get-LocalUser | Where-Object -Property "Enabled" -like "False"
```
### Mostra informações do usuário chamado "smith"
```
Get-LocalUser -Name "smith"
```
### Lista grupos locais do sistema
```
Get-LocalGroup
```
### Lista membros do grupo "Administradores"
```
Get-LocalGroupMember -Name Administradores
```
### Exibe detalhes do usuário "smith" em formato de lista
```
Get-LocalUser -name smith | Format-List
```
### Exibe apenas propriedades específicas do usuário "smith"
```
Get-LocalUser -name smith | Select-Object FullName, Enabled, Name, SID
```
### Mostra configuração de rede (IPs, gateways, etc.)
```
Get-NetIPConfiguration
```
### Lista endereços IP configurados
```
Get-NetIPAddress
```
### Exibe conexões TCP ativas
```
Get-NetTCPConnection
```
### Lista processos em execução
```
Get-Process
```
### Lista serviços do sistema
```
Get-Service
```
### Filtra serviços que estão em execução
```
Get-Service | findstr Running
```
### Calcula e mostra o hash do arquivo
```
Get-FileHash -Path .\new.txt
```

## Active Directory (AD) Enumeration

### Baixando o Power View:
```
wget https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/refs/heads/master/Recon/PowerView.ps1
```
### Executando o powershell com bypass da execução de scripts
```
powershell -ep bypass
```
### Importando o módulo PowerView
```
. .\PowerView.ps1
```
### Enumeração de Domínio
- Enumeração de Domínio

Obtém informações sobre o domínio atual ou especificado
```
Get-Domain
```
Lista os controladores de domínio
```
Get-DomainController
```
Enumera relações de confiança entre domínios
```
Get-DomainTrust
```
Retorna informações sobre a floresta AD
```
Get-Forest
```
Lista todos os domínios dentro da floresta
```
Get-ForestDomain
```
Mostra relações de confiança entre florestas
```
Get-ForestTrust
```

- Usuários e Grupos

Enumera usuários do AD com atributos detalhados.
```
Get-DomainUser
```
Lista grupos do AD
```
Get-DomainGroup
```
Mostra membros de um grupo específico
```
Get-DomainGroupMember
```
Identifica onde usuários estão logados
```
Find-DomainUserLocation
```
Obtém ACLs associadas a objetos de usuários/grupos.
```
Get-DomainObjectAcl
```

- Computadores e Sessões
Lista computadores do domínio
```
Get-DomainComputer
```
Mostra sessões ativas em máquinas remotas
```
Get-NetSession
```
Enumera usuários logados em um computador remoto
```
Get-NetLoggedon
```
Verifica usuários logados localmente
```
Get-LoggedOnLocal
```
Busca processos em execução em máquinas do domínio
```
Find-DomainProcess
```

- ACLs e Permissões
Obtém ACLs de objetos no AD
```
Get-DomainObjectAcl
```
Adiciona permissões a objetos
```
Add-DomainObjectAcl
```
Remove permissões
```
Remove-DomainObjectAcl
```
Escaneia ACLs em busca de permissões excessivas
```
Invoke-ACLScanner
```

- Compartilhamentos e Serviços
Lista compartilhamentos de rede em computadores.
```
Get-NetShare
```
Enumera servidores de arquivos
```
Get-NetFileServer
```
Lista serviços em execução em máquinas remotas
```
Get-NetService
```
Busca compartilhamentos acessíveis no domínio
```
Find-DomainShare
```

- Reconhecimento Avançado
Identifica máquinas onde o usuário atual tem acesso de administrador local.
```
Find-LocalAdminAccess
```
Localiza onde usuários específicos estão logados
```
Invoke-UserHunter
```
Localiza processos específicos em máquinas do domínio
```
Invoke-ProcessHunter
```
Busca compartilhamentos acessíveis
```
Invoke-ShareFinder
```
Enumera administradores locais em máquinas remotas.
```
Invoke-EnumerateLocalAdmin
```

### Considerações Importantes
• O PowerView é uma ferramenta de pentest/red team e também usada em pesquisas de segurança.
• Seu uso em ambientes sem autorização pode ser considerado atividade maliciosa.
• Em ambientes corporativos, é utilizado para auditoria de segurança e identificação de configurações incorretas no Active Directory

## Bloodhound com SharpHound

### Baixando o SharpHound:
```
wget https://raw.githubusercontent.com/BloodHoundAD/BloodHound/refs/heads/master/Collectors/SharpHound.ps1
```
### Importando o módulo SharpHound:
```
. .\SharpHound.ps1
```
### Extraindo dados do AD
```
Invoke-BloodHound -CollectionMethods All -Domain dominio.com -ZipFilename dominio.zip
```

# Aviso de Isenção de Responsabilidade – Material de Red Team
Este material destina-se exclusivamente a fins educacionais, acadêmicos e de conscientização em segurança da informação. As técnicas, exemplos e cenários aqui descritos têm como objetivo demonstrar vulnerabilidades potenciais e auxiliar profissionais de segurança na prevenção, detecção e resposta a ameaças.
• Não é permitido utilizar este conteúdo para atividades ilegais, maliciosas ou que violem políticas corporativas, regulamentos ou legislações vigentes.
• O uso indevido das informações apresentadas pode resultar em sanções legais, disciplinares e criminais.
• Os autores e distribuidores deste material não se responsabilizam por qualquer dano, perda ou consequência decorrente da aplicação inadequada ou não autorizada das técnicas descritas.
• Recomenda-se que qualquer prática de red team seja realizada em ambientes controlados, autorizados e com consentimento explícito das partes envolvidas.
