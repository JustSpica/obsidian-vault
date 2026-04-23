# ICMP

ICMP (Internet Control Message Protocol) é o protocolo de controle usado com [[IPv4]] para **sinalizar erros** e fornecer alguns serviços auxiliares (ex.: echo/ping). No cabeçalho IPv4, ele aparece no campo **Protocolo** como `0x01`.

Tanenbaum define que quando um roteador ou host encontra um problema ao encaminhar/entregar um datagrama IP, ele pode avisar o emissor via ICMP. 

ICMP não “conserta” o IP, ele apenas informa.

**Exemplo cabeçalho ICMP:** ![[exemplo_cabecalho_icmp.png]]

- **Tipo (8 bits)**
	- `0` = Resposta de echo (resposta ao ping).
	- `3` = Destino não acessível.
	- `5` = *Redirect*, informando nova rota. Um roteador diz “use outro gateway”. Em redes reais, costuma ser desabilitado/filtrado por segurança.
	- `8` = Solicitação de echo (ping. Usado para medir alcane e latência).
	- `11` = TTL excedeu. Aparece em loops de roteamento e é o fundamento do `traceroute`.
	- `17` = Solicitação de máscara.
	- `18` = Resposta de máscara.
- **Code (8 bits):** O código depende do tipo que será enviado, por exemplo, quando `Tipo = 3`:
	- `0`: Rede inacessível.
	- `1`: Host inacessível.
	- `2`: Protocolo inacessível.
	- `3`: Porta inacessível.
	- `4`: [[IPv4|Fragmentação]] necessária, mas pacote tinha `DF = 1`.
	- `6`: Rede destino desconhecida.
	- `7`: Host destino desconhecido.
- **Checksum (16 bits)**

O restante depende do tipo/mensagem.

Em mensagens de erro, é comum o ICMP carregar parte do datagrama original (tipicamente o [[IPv4|cabeçalho IP + os primeiros bytes do payload]]) para o emissor conseguir identificar qual comunicação gerou o erro.

Tanenbaum comenta que, incluir o cabeçalho IP original + os primeiros 8 bytes do payload costuma ser suficiente para a [[Modelos OSI e TCP IP|camada de transporte]] identificar a conexão/porta afetada.

*OBS: ICMP é carregado dentro de um datagrama IP como payload (não é “fora” do cabeçalho IP).*
## Referências

- Baseado no PDF do La salle [[redes-aula-11.pdf|Redes - Aula 11]].
- Baseado no livro [[livro-tanenbaum.pdf|Redes de computadores de Tanenbaum]].
