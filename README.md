# WireShark: 6 filtros para aplicação no aplicativo :shark:

## 1º filtro: tcp.analysis.flags

Teoria - 
Protocolo TCP:
- Transmission Control Protocol (TCP) é um protocolo de transporte confiável que garante a entrega ordenada de pacotes de dados entre um remetente e um destinatário.
- TCP utiliza um mecanismo de controle de fluxo e de erro para garantir que os dados sejam entregues corretamente.
- TCP estabelece uma conexão através do processo conhecido como "three-way handshake" e termina a conexão de forma ordenada.

Funcionamento -
Flags TCP:  Os flags são bits de controle no cabeçalho TCP que indicam o estado ou o propósito de um pacote TCP.
- SYN: Sinaliza o início de uma conexão.
- ACK: Confirma o recebimento de pacotes.
- FIN: Sinaliza o término de uma conexão.
- RST: Reinicia a conexão.
- PSH: Indica que os dados devem ser empurrados imediatamente ao aplicativo.
- URG: Indica dados urgentes.

Uso:
- Esse filtro é utilizado para identificar pacotes TCP que têm flags específicos definidos, indicando eventos ou estados importantes na comunicação TCP, como retransmissões, pacotes fora de ordem, e outros problemas ou condições especiais.

## 2º filtro: dns or http

Teoria:

Protocolo DNS:
- Domain Name System (DNS) é responsável pela resolução de nomes de domínio para endereços IP.
- As consultas DNS transformam nomes de domínio amigáveis (como www.exemplo.com) em endereços IP necessários para o roteamento de rede.

Protocolo HTTP:
- HyperText Transfer Protocol (HTTP) é utilizado para comunicação entre navegadores web e servidores.
- Funciona no modelo de requisição e resposta, onde o cliente faz uma requisição e o servidor responde com os dados solicitados.

Funcionamento:

DNS:
- Consulta: Um cliente envia uma consulta DNS para resolver um nome de domínio.
- Resposta: O servidor DNS responde com o endereço IP correspondente.

HTTP:
- Requisição: O cliente envia uma requisição HTTP (GET, POST, etc.).
- Resposta: O servidor responde com o conteúdo solicitado (página web, dados, etc.).

Uso:

- Esse filtro é usado para exibir apenas os pacotes DNS e HTTP na captura, facilitando a análise do tráfego de navegação web e resolução de nomes de domínio.


## 3º filtro: !(arp or icmp or dns)

Teoria:

Protocolo ARP:
- Address Resolution Protocol (ARP) é usado para mapear endereços IP para endereços MAC (Media Access Control) em redes locais.
Protocolo ICMP:
- Internet Control Message Protocol (ICMP) é utilizado para enviar mensagens de erro e operações de diagnóstico (como ping) entre dispositivos de rede.

Funcionamento:

ARP:
- Solicitação ARP: Um dispositivo solicita o endereço MAC correspondente a um endereço IP.
- Resposta ARP: O dispositivo com o endereço IP correspondente responde com seu endereço MAC.
ICMP:
- Echo Request/Reply: Utilizado para verificar a conectividade (ping).
- Mensagens de Erro: Indicando problemas de roteamento ou entrega de pacotes.

Uso:
- Esse filtro é usado para excluir pacotes ARP, ICMP e DNS, permitindo a análise de outros tipos de tráfego na rede.

## 4º filtro: tcp.analysis.retransmission

Teoria:

Funcionamento:

- O TCP é um protocolo de transporte confiável que garante a entrega de dados na ordem correta. Para fazer isso, ele usa um mecanismo de confirmação (ACK) para garantir que os pacotes foram recebidos corretamente.
- Quando um pacote é enviado, o remetente aguarda um ACK do destinatário. Se o ACK não for recebido dentro de um tempo especificado (timeout), o remetente presume que o pacote foi perdido ou corrompido e retransmite o pacote.
- Wireshark identifica essas retransmissões usando o filtro tcp.analysis.retransmission.

Uso:

- O filtro tcp.analysis.retransmission é uma ferramenta poderosa no Wireshark para identificar e analisar retransmissões de pacotes TCP. Compreender o funcionamento do protocolo TCP e a importância das retransmissões ajuda a diagnosticar problemas de rede, melhorar o desempenho e garantir a segurança da rede.

## 5º filtro: frame contains "attachment" or frame contains "pdf"

## 6º filtro: ip.addr==127.0.0.1 (abertura e visualização de portas)

nmap 127.0.0.1 ou nmap localhost

ncat -l 1001 (para abrir a porta 1001)
ncat 127.0.0.1 1001 (para fechar a porta)

1. https://nmap.org/download.html

2. https://get-site-ip.com

3. https://www.youtube.com/watch?v=KrNWKxLk5No

## filtro extra: tls.handshake.extensions_server_name contains "amazon.com" 👨‍👦
