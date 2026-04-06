# Comandos Básicos do Windows

- Exibir a localização
- Navegação entre os diretórios
- Listagem de arquivos e diretórios
- Criação de diretórios
- Exibir saída na tela
- Enviar a saída para um arquivo
- Adicionar conteúdo a um arquivo
- Lendo conteúdo de um arquivo
- Abrindo arquivos pelo prompt
- Copiando, movendo e apagando arquivos
- Atributos de arquivos
- Tornando um diretório oculto
- Criando e apagando diretórios
- Networking
- Verificando conexões de rede
- Listando tarefas
- Gerenciando usuários
- Baixando arquivos

## Exibir a localização
```
C:\Windows\system32> echo %cd%
C:\Windows\system32
```
```
C:\Windows\system32> cd
C:\Windows\system32
```

## Navegação entre os diretórios
```
C:\Windows\system32> cd ..
C:\Windows>cd system32
C:\Windows\System32> cd \
C:\>
```

## Listagem de arquivos e diretórios
```
C:\> dir
C:\> dir c:\users\
```

## Criação de diretórios
```
C:\> cd Users\admin\Desktop
C:\Users\admin\Desktop> mkdir redscan
```

## Exibir saída na tela
```
C:\Users\admin\> echo RedScan-Academy
RedScan-Academy
```

## Enviar a saída para um arquivo
```
C:\> echo RedScan-Academy > red.txt
```

## Adicionar conteúdo a um arquivo
```
C:\> echo Aula-PowerShell >> red.txt
```

## Lendo conteúdo de um arquivo
```
C:\> type red.txt
RedScan-Academy
Aula-PowerShell
```

## Abrindo arquivos pelo prompt
```
C:\> notepad red.txt
```

## Copiando, movendo e apagando arquivos
```
C:\> copy red.txt redscan.txt
        1 file(s) copied.

C:\> move red.txt ..\banner.txt
        1 file(s) moved.

C:\> del redscan.txt
```

Atributos de arquivos
```
C:\> attrib /?
+ Define um atributo.
-  Limpa um atributo.
H Atributo de arquivo oculto.

C:\> attrib +H banner.txt

C:\> attrib -H banner.txt
```
## Tornando um diretório oculto
```
C:\Users\admin\Desktop> attrib +H redscan

C:\Users\admin\Desktop> attrib -H redscan
```

## Criando e apagando diretórios
```
C:\> mkdir pasta

C:\> rmdir pasta

C:\> rmdir redscan
The directory is not empty.

C:\> rmdir /s redscan
redscan, Are you sure (Y/N)? Y
```

## Networking
```
C:\> ipconfig

C:\> ipconfig /all
```

## Verificando conexões de rede
```
C:\>netstat /?
-a Displays all connections and listening ports.
-n Displays addresses and port numbers in numerical form.
-o Displays the owning process ID associated with each connection.
-p proto Shows connections for the protocol specified by proto

C:\>netstat -ano

C:\>netstat -p tcp

C:\>netstat -p udp

C:\>netstat -anop tcp

C:\>netstat -anop udp
```

## Listando tarefas
```
c:\>tasklist
CalculatorApp.exe   7352    Console    1    73,988 K

c:\>taskkill -pid 7352
SUCCESS: Sent termination signal to the process with PID 7352.

c:\>taskkill -pid 7352 /f
SUCCESS: The process with PID 7352 has been terminated.
```

## Gerenciando usuários
```
C:\> net user

C:\> net user smith Senha@123 /add

C:\> net user smith

C:\> net localgroup

C:\> net localgroup administrators smith /add

C:\> net localgroup administrators

C:\> net user smith

C:\> net localgroup administrators smith /delete

C:\> net user smith /delete

C:\> net user
```

## Baixando arquivos
cmd = certutil -urlcache -split -f  
link = https://raw.githubusercontent.com/smithbraz/windows/refs/heads/main/scripts-powershell/info.ps1
file = info.ps1

```
C:\Users\admin> certutil -urlcache -split -f https://raw.githubusercontent.com/smithbraz/windows/refs/heads/main/scripts-powershell/info.ps1 info.ps1

C:\Users\admin> dir
03/27/2026    06:17 PM   834   info.ps1

C:\Users\admin> type info.ps1
```

BITSADMIN

O utilitário BITSAdmin é uma ferramenta de linha de comando antiga do Windows que permite gerenciar transferências de arquivos usando o serviço Background Intelligent Transfer Service (BITS).
```
bitsadmin /transfer MeuJob /download /priority normal https://raw.githubusercontent.com/smithbraz/windows/refs/heads/main/scripts-powershell/info.ps1 C:\Users\admin\info.ps1
```
Detalhes:
• `bitsadmin`	→ chama o utilitário.
• `/transfer MeuJob`	→ cria uma tarefa de transferência com o nome "MeuJob".
• `/download`	→ indica que é um download.
• `/priority normal`	→ define a prioridade da tarefa.
• `https://raw.githubusercontent.com/smithbraz/windows/refs/heads/main/scripts-powershell/info.ps1`	→ URL do arquivo a ser baixado.
• `C:\Users\admin\info.ps1`	→ caminho local onde o arquivo será salvo.


# Aviso de Isenção de Responsabilidade – Material de Red Team
Este material destina-se exclusivamente a fins educacionais, acadêmicos e de conscientização em segurança da informação. As técnicas, exemplos e cenários aqui descritos têm como objetivo demonstrar vulnerabilidades potenciais e auxiliar profissionais de segurança na prevenção, detecção e resposta a ameaças.
• Não é permitido utilizar este conteúdo para atividades ilegais, maliciosas ou que violem políticas corporativas, regulamentos ou legislações vigentes.
• O uso indevido das informações apresentadas pode resultar em sanções legais, disciplinares e criminais.
• Os autores e distribuidores deste material não se responsabilizam por qualquer dano, perda ou consequência decorrente da aplicação inadequada ou não autorizada das técnicas descritas.
• Recomenda-se que qualquer prática de red team seja realizada em ambientes controlados, autorizados e com consentimento explícito das partes envolvidas.

