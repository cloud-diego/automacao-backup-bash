#  🐧 Scripts Bash no Linux (AWS EC2)

Este projeto documenta um laboratório prático em uma instância Amazon Linux EC2, com foco na automação de tarefas por meio de scripts Bash. O objetivo foi aprender a criar um script que realiza o backup de uma pasta e a executá-lo, o que é fundamental para a automação de rotinas em ambientes Linux.

## 🛠️ Tecnologias Utilizadas

<div align="left"> 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="AWS" width="50" height="50"/> 
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux" width="50" height="50"/>
</div>

## 🎯 Objetivos

- Criar um script Bash para automatizar o backup de uma pasta. 
- Conceder permissões de execução ao script. 
- Executar o script e validar a criação do arquivo de backup compactado. 

## 🚀 Ambiente

- **Serviço:** Amazon EC2 
- **Tipo de instância:** t3.micro 
- **Sistema Operacional:** Amazon Linux 2 
- **Acesso:** SSH (via .pem ou .ppk) 

## 📌 Etapas do Laboratório

### 1. Conexão via SSH  

Baixei a chave de acesso (.pem para Mac/Linux ou .ppk para Windows). 

Altere as permissões da chave: 
```bash
chmod 400 labsuser.pem
```

Conectei-me à instância usando o comando: 
```bash
ssh -i labsuser.pem ec2-user@<public-ip>
```

### 2. Criação do Script de Backup  

Após me conectar, criei o arquivo do script chamado `backup.sh` com o comando `touch` e adicionei permissões de execução com: 
```bash
sudo chmod 755 backup.sh
```

Utilizei o **vi** para escrever o código: 
```bash
#!/bin/bash

DAY="$(date +%Y_%m_%d)"

BACKUP="/home/$USER/backups/$DAY-backup-CompanyA.tar.gz"

tar -csvpzf $BACKUP /home/$USER/CompanyA
```

### 3. Execução e Validação  

Executei o script com o comando: 
```bash
./backup.sh
```

Ele mostrou o progresso da compactação. 

Para confirmar que o backup havia sido criado, usei o comando: 
```bash
ls backups/
```

Esse comando listou o arquivo `.tar.gz` com o nome e data corretos na pasta `backups`.

