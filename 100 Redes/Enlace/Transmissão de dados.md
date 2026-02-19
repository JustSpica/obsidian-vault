# Modos de transmissão de dados

Descrevem como o fluxo de comunicação acontece entre dispositivos.
## Escopo do fluxo de dados

Definem para quem uma mensagem enviada em uma rede é destinada, determinando quem recebe os dados.

Existem três modos:

1. **Unicast:** Transmite apenas para um único dispositivo. Sempre que o byte mais significativo for par é unicast. Ex: `02:05:04:03:2E:4A`
2. **Multicast:** Transmite para um grupo específico de dispositivos. Sempre que o byte mais significativo for impar é multicast. Ex: `01:00:5E:XX:XX:XX`
3. **Broadcast:** Transmite para todos os dispositivos na rede local, sendo limitado ao domínio de broadcast. Ex: `FF:FF:FF:FF:FF:FF`
## Direção de fluxo de dados

Determina como dispositivos se comunicam entre si, em simultaneidade e sentido. A ideia é como posso gerenciar o fluxo de sinais elétricos/ópticos em um canal físico compartilhado ou dedicado.

Existem três modos:

1. **Simplex:** Ocorre em uma direção fixa, com transmissor e receptor. Exemplo: transmissão de rádio ou TV.
2. **Half-Duplex:** Bidirecional, mas não simultaneamente. Os dispositivos se refezam entre transmissor e receptor. Exemplo: walkie-talkie
3. **Full-Duplex:** Bidirecional simultâneo. Nesse caso requer dois canais físicos separados (um par de fios trançados ou dois cabos ópticos) ou multiplexação de frequência no caso de fibra ópica. Exemplo: switch moderno, telefonia, ethernet via par trançado (cat5e+)
## Referências

- Baseado no PDF do La salle [[redes-aula-01.pdf|Redes - Aula 01]].