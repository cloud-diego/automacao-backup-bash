#  🐧 Automação de backups em Linux com script Bash (AWS EC2)

Este projeto documenta um laboratório prático em uma instância Amazon Linux EC2, com foco na automação de tarefas por meio de scripts Bash. O objetivo foi aprender a criar um script que realiza o backup de uma pasta e a executá-lo, o que é fundamental para a automação de rotinas em ambientes Linux.

# 📂 **Estrutura do Projeto**

```
automacao-backup-bash/
│
├── imagens/
│
└── README.md
│
└── backups.sh
```


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

<img width="1302" height="734" alt="01-conexao-ssh" src="https://github.com/user-attachments/assets/29d7c102-7e4d-4115-8313-be606a85fc77" />

### 2. Criação do Script de Backup  

Após me conectar, criei o arquivo do script chamado `backups.sh` com o comando `touch` e adicionei permissões de execução com: 
```bash
sudo chmod 755 backups.sh
```

<img width="1302" height="734" alt="02-criacao-arquivo" src="https://github.com/user-attachments/assets/0f712a41-a5bb-4005-bc19-e937d009b309" />

Utilizei o **vi** para escrever o código: 
```bash
#!/bin/bash

DAY="$(date +%Y_%m_%d)"

BACKUP="/home/$USER/backups/$DAY-backup-CompanyA.tar.gz"

tar -csvpzf $BACKUP /home/$USER/CompanyA
```

<img width="1302" height="734" alt="03-codigo-bash" src="https://github.com/user-attachments/assets/5598233c-cae6-4f7e-b602-87cfc8425df6" />

### 3. Execução e Validação  

Executei o script com o comando: 
```bash
./backups.sh
```

Ele mostrou o progresso da compactação.

<img width="1302" height="734" alt="04-execucao-script" src="https://github.com/user-attachments/assets/b4f130b5-6c91-4f4d-8e8b-81c409759656" />


Para confirmar que o backup havia sido criado, usei o comando: 
```bash
ls backups/
```
<img width="1302" height="734" alt="05-confirmacao-backup" src="https://github.com/user-attachments/assets/36b585a8-6d85-467b-9d24-93f1524014a0" />

Esse comando listou o arquivo `.tar.gz` com o nome e data corretos na pasta `backups`.

