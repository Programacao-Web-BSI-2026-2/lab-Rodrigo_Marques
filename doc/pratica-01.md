# Registro de Prática 01 — Protocolo HTTP & Sockets Bare-Metal

**Aluno:** Rodrigo De Souza Marques  
**Curso:** Bacharelado em Sistemas de Informação  

## Resumo da Atividade
Nesta prática de laboratório, exploramos o funcionamento do protocolo **HTTP/1.1** diretamente sobre a camada de transporte (**TCP**) utilizando as ferramentas **Netcat** e **cURL**. O objetivo foi compreender como as mensagens são estruturadas, transmitidas e interpretadas entre cliente e servidor sem as abstrações de um navegador.

### Principais Experimentos e Resultados
* **Ciclo de Vida e Cabeçalho `Host`:** Mapeamos o *Three-Way Handshake* TCP (`SYN`, `SYN-ACK`, `ACK`) e confirmamos que o envio de uma requisição HTTP/1.1 sem o cabeçalho `Host:` resulta no erro `400 Bad Request`, pois o servidor não consegue identificar o destino da solicitação.
* **Métodos HTTP:** Diferenciamos a semântica dos verbos principais: `GET` (recuperar dados), `POST` (enviar/inserir dados no servidor) e `OPTIONS` (consultar as opções de comunicação suportadas pelo recurso).
* **Codificação de URL (Percent-Encoding):** Analisamos como caracteres fora da tabela ASCII padrão são convertidos para UTF-8 em hexadecimal na URL (como `%20` para espaço e `%C3%A7` para `ç`).
* **Negociação de Conteúdo (`User-Agent` e `Accept`):** Testamos o envio de cabeçalhos personalizados para simular diferentes clientes/navegadores e indicar os formatos de resposta esperados.
* **Redirecionamentos:** Verificamos o comportamento do `curl -I` diante de respostas `302 Found`, onde a flag `-L` instrui o cliente a seguir automaticamente o endereço indicado no cabeçalho `Location` até obter o status `200 OK`.

## Conclusão
A prática reforçou a importância de dominar a sintaxe textual do HTTP (como o uso de delimitadores `CRLF` e cabeçalhos) para diagnosticar falhas de comunicação, otimizar o tráfego de rede e construir aplicações web e sistemas distribuídos mais robustos.
