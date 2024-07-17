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

Funcionamento:

- O TCP é um protocolo de transporte confiável que garante a entrega de dados na ordem correta. Para fazer isso, ele usa um mecanismo de confirmação (ACK) para garantir que os pacotes foram recebidos corretamente.
- Quando um pacote é enviado, o remetente aguarda um ACK do destinatário. Se o ACK não for recebido dentro de um tempo especificado (timeout), o remetente presume que o pacote foi perdido ou corrompido e retransmite o pacote.
- Wireshark identifica essas retransmissões usando o filtro tcp.analysis.retransmission.

Uso:

- O filtro tcp.analysis.retransmission é uma ferramenta poderosa no Wireshark para identificar e analisar retransmissões de pacotes TCP. Compreender o funcionamento do protocolo TCP e a importância das retransmissões ajuda a diagnosticar problemas de rede, melhorar o desempenho e garantir a segurança da rede.

## 5º filtro: frame contains "attachment" or frame contains "pdf"

Teoria:

- O filtro frame contains não se limita a um protocolo específico. Ele procura por uma string de texto dentro do conteúdo de qualquer quadro (frame) capturado. Isso significa que pode ser aplicado a qualquer pacote de rede, independentemente do protocolo.

Funcionamento:

- Wireshark captura todo o tráfego de rede que passa pela interface de rede selecionada.
- O filtro frame contains procura dentro do conteúdo de cada quadro capturado para verificar se ele contém a string especificada.

Uso:

- Este filtro pode ser usado para monitorar anexos de email, transferências de arquivos PDF e para fins de segurança da rede. Ao aplicá-lo, você pode obter insights valiosos sobre o tráfego de rede e detectar atividades específicas relacionadas a anexos e arquivos PDF.

## 6º filtro: ip.addr==127.0.0.1 (abertura e visualização de portas)

Teoria e Funcionamento:

- Utilizado no Wireshark para identificar pacotes cujo endereço IP de origem ou destino é 127.0.0.1, também conhecido como o endereço de loopback ou localhost. Este endereço é usado para testes e diagnósticos dentro do próprio dispositivo.

Teste:

- Para utilizar este filtro e testar suas funcionalidades reais, podemos seguir os seguintes passos:

  1. Baixar e instalar o Nmap (Network Mapper);
  2. Executar o Nmap para escanear as portas do localhost;
  3. Abrir uma nova porta no localhost;
  4. Fechar essa porta criada;
  5. Verificar o Wireshark, com o filtro 6.
 
### 1. BAIXAR E INSTALAR O NMAP

ACESSAR https://nmap.org/download.html
BAIXAR A VERSÃO COMPATÍVEL COM SEU SISTEMA OPERACIONAL
INSTALAR DE ACORDO COM AS INSTRUÇÕES DO SITE OFICIAL

### 2. EXECUTAR O NMAP PARA ESCANEAR AS PORTAS DO LOCALHOST

ABRIR O TERMINAL COMO ADMINISTADOR
EXECUTAR O SEGUINTE COMANDO PARA ESCANEAR AS PORTAS DO LOCALHOST:

    nmap 127.0.0.1
ou
    
    nmap localhost

### 3. ABRIR UMA NOVA PORTA NO LOCALHOST

ABRIR OUTRA ABA DO TERMINAL, COMO ADMINISTADOR
EXECUTAR O SEGUINTE COMANDO PARA CRIAR UMA NOVA PORTA NO LOCALHOST:

    ncat -l nº_da_porta

### 4. FECHAR ESSA PORTA CRIADA

NA ABA DO TERMINAL QUE USAMOS O NMAP, EXECUTAR O SEGUINTE COMANDO PARA CRIAR UMA NOVA PORTA NO LOCALHOST:

    ncat 127.0.0.1 nº_da_porta

### 5.VERIFICAR O WIRESHARK, COM O FILTRO 6

A PORTA 1001 DEVERÁ APARECER SENDO USADA EM ALGUM PROTOCOLO TCP!!!

Uso:

- O filtro ip.addr == 127.0.0.1 no Wireshark é útil para capturar e analisar pacotes de loopback, permitindo que você examine a comunicação interna no dispositivo.


## filtro extra: tls.handshake.extensions_server_name contains "amazon.com" 👨‍👦

## 
Links úteis:

1. https://nmap.org/download.html
   
3. https://www.youtube.com/watch?v=KrNWKxLk5No
