# dvwa-bruteforce-hydra-lab
Ataque de força bruta com Hydra em (DVWA).

---

🔐 Projeto DIO - Ataque de Força Bruta com Hydra em DVWA

📌 Descrição

Este projeto demonstra a execução de um ataque de força bruta em uma aplicação web vulnerável (DVWA - Damn Vulnerable Web Application), utilizando a ferramenta Hydra.

O objetivo foi identificar credenciais válidas explorando a ausência de mecanismos de proteção contra múltiplas tentativas de autenticação.


---

🧠 Ambiente Utilizado

Devido à limitação de hardware (uso de celular), o ambiente foi adaptado:


🎯 Alvo: DVWA

📱 Dispositivo: Android

🌐 Plataforma: TryHackMe

🔐 VPN: OpenVPN (TryHackMe)

🖥️ Ambiente Linux: UserLAnd (Ubuntu)



---

🛠️ Ferramentas Utilizadas

Nmap → Enumeração de portas e serviços

Hydra → Ataque de força bruta em formulário web


---

🔍 Enumeração

Foi realizada a identificação de serviços ativos no alvo:

nmap -p 80,443 10.64.160.77

Resultado:

Porta 80 (HTTP) aberta

---

🌐 Acesso à Aplicação

A aplicação DVWA foi acessada via navegador:

http://10.64.160.77

Login padrão:

admin / password

O nível de segurança foi configurado como:

LOW

---

⚔️ Ataque de Força Bruta

O ataque foi realizado no módulo:

/vulnerabilities/brute/

⚠️ Desafio Encontrado

Inicialmente, o Hydra retornava múltiplas senhas válidas (falso positivo), devido à ausência do cookie de sessão.

---

🍪 Uso de Cookie de Sessão

Foi necessário capturar o cookie de autenticação:

PHPSESSID=g2urb7k0lf2igvvbi1uuto9gk5; security=low

---

💻 Comando Utilizado

hydra -l admin -P senhas.txt 10.64.160.77 http-get-form "/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:F=Username and/or password incorrect.:H=Cookie: PHPSESSID=g2urb7k0lf2igvvbi1uuto9gk5; security=low"

---

✅ Resultado

O Hydra identificou a credencial válida:

login: admin

password: password

---

⚠️ Vulnerabilidades Identificadas


• Exposição a ataques de força bruta

• Ausência de autenticação multifator (MFA)

• Ausência de limitação de tentativas de login

---

🛡️ Medidas de Mitigação

• Utilizar CAPTCHA

• Monitorar tentativas suspeitas

• Adotar autenticação multifator (MFA)

• Implementar bloqueio após múltiplas tentativas

---

📊 Conclusão

O teste demonstrou que aplicações sem mecanismos de proteção adequados são altamente vulneráveis a ataques de força bruta.

Além disso, foi necessário o uso de uma sessão autenticada (PHPSESSID) para execução correta do ataque, evidenciando a importância do gerenciamento seguro de sessões.

---

🚀 Observação Final

Este projeto foi realizado inteiramente em ambiente mobile, demonstrando a viabilidade de execução de testes de segurança mesmo com limitações de hardware.

---


👩‍💻 Autora

Projeto desenvolvido por " Kelwri Jheine "
