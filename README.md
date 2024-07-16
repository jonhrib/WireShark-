# WireShark: 6 filtros para aplicação no aplicativo

### 1º filtro tcp.analysis.flags

Teoria:
Protocolo TCP:
- Transmission Control Protocol (TCP) é um protocolo de transporte confiável que garante a entrega ordenada de pacotes de dados entre um remetente e um destinatário.
- TCP utiliza um mecanismo de controle de fluxo e de erro para garantir que os dados sejam entregues corretamente.
- TCP estabelece uma conexão através do processo conhecido como "three-way handshake" e termina a conexão de forma ordenada.

Funcionamento:
Flags TCP:  Os flags são bits de controle no cabeçalho TCP que indicam o estado ou o propósito de um pacote TCP.
- SYN: Sinaliza o início de uma conexão.
- ACK: Confirma o recebimento de pacotes.
- FIN: Sinaliza o término de uma conexão.
- RST: Reinicia a conexão.
- PSH: Indica que os dados devem ser empurrados imediatamente ao aplicativo.
- URG: Indica dados urgentes.

Uso:
- Esse filtro é utilizado para identificar pacotes TCP que têm flags específicos definidos, indicando eventos ou estados importantes na comunicação TCP, como retransmissões, pacotes fora de ordem, e outros problemas ou condições especiais.

### 2º filtro* dns or http

### 3º filtro* !(arp or icmp or dns)

### 4º filtro* 

### 5º filtro* 

### 6º filtro* 

1. https://nmap.org/download.html

2. https://get-site-ip.com

3. https://www.youtube.com/watch?v=KrNWKxLk5No
