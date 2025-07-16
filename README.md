# intrusion_detection
Intrusion Detection with Kali Linux

Análise básica de intrusão com Kali Linux
📍 1. Verifique conexões e processos ativos
bash
Copy
Edit
sudo netstat -tunap
sudo ss -tulnp
ps aux --sort=-%cpu
Procure por:

Conexões com IPs suspeitos

Processos desconhecidos ou fora do padrão

Programas rodando como root sem motivo

📍 2. Liste usuários e acessos recentes
bash
Copy
Edit
last
who
cat /etc/passwd
Verifique:

Logins suspeitos

Criação de usuários não autorizados

Acesso em horários estranhos

📍 3. Verifique alterações recentes no sistema
bash
Copy
Edit
sudo find / -type f -ctime -2 2>/dev/null  # Arquivos criados/modificados nos últimos 2 dias
E veja se houve scripts ou binários alterados.

📍 4. Cheque logs do sistema
bash
Copy
Edit
sudo cat /var/log/auth.log
sudo journalctl -xe
Procure por:

Falhas de login (Failed password)

Usuários com acesso root

Atividades SSH suspeitas

📍 5. Procure rootkits e backdoors
bash
Copy
Edit
sudo chkrootkit
sudo rkhunter --check
Essas ferramentas detectam alterações críticas no sistema feitas por malware.

📍 6. Capture e analise tráfego de rede
Captura com tcpdump:
bash
Copy
Edit
sudo tcpdump -i eth0 -w captura.pcap
Análise no Wireshark:
bash
Copy
Edit
wireshark captura.pcap
Filtre por:

http, ftp, dns, smtp

IPs ou domínios desconhecidos

Transmissão de senhas ou arquivos

📍 7. Escaneie a própria máquina com Nmap
bash
Copy
Edit
sudo nmap -sS -sV -O localhost
Isso mostra:

Portas abertas

Serviços ativos

Possível sistema operacional

Se você mesmo foi comprometido com algum serviço malicioso

📍 8. Busque arquivos escondidos e scripts suspeitos
bash
Copy
Edit
find / -name ".*" 2>/dev/null  # Arquivos ocultos
find /home -name "*.sh"
find /tmp -type f
🧪 Extra: Ferramentas visuais de forense
Autopsy:

bash
Copy
Edit
autopsy
Abre no navegador uma interface completa de análise forense de disco.

Volatility (análise de memória RAM):

bash
Copy
Edit
volatility -f memoria.dump imageinfo
Requer uma dump de memória (.raw, .dump)
