# Modos de transmissão de dados

Descrevem como o fluxo de comunicação acontece entre dispositivos.
## Escopo do fluxo de dados

Definem para quem uma mensagem enviada em uma rede é destinada, determinando quem recebe os dados.

Existem três modos:

1. **Unicast:** Transmite apenas para um único dispositivo.
2. **Multicast:** Transmite para um grupo específico de dispositivos.
3. **Broadcast:** Transmite para todos os dispositivos na rede local, sendo limitado ao domínio de broadcast.
## Direção de fluxo de dados

Determina como dispositivos se comunicam entre si, em simultaneidade e sentido. A ideia é como posso gerenciar o fluxo de sinais elétricos/ópticos em um canal físico compartilhado ou dedicado.

Existem três modos:

1. **Simplex:** Ocorre em uma direção fixa, com transmissor e receptor. Exemplo: transmissão de rádio ou TV.
2. **Half-Duplex:** Bidirecional, mas não simultaneamente. Os dispositivos se refezam entre transmissor e receptor. Exemplo: walkie-talkie
3. **Full-Duplex:** Bidirecional simultâneo. Nesse caso requer dois canais físicos separados (um par de fios trançados ou dois cabos ópticos) ou multiplexação de frequência no caso de fibra ópica. Exemplo: switch moderno, telefonia, ethernet via par trançado (cat5e+)