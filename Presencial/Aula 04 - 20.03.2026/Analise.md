# Atividade:

Com base nos conceitos estudados sobre Sistemas Digitais de Controle Distribuído (SDCD), realize uma análise de como um sistema desse tipo poderia ser aplicado no projeto integrador. Considere o seguinte exemplo de arquitetura tecnológica:

Sensor de Temperatura → ESP32 → MQTT → Servidor → Aplicativo Mobile → Dashboard → Gestão da Fábrica

A partir desse fluxo, descreva e analise:
1. O papel de cada componente do sistema (sensor, ESP32, protocolo MQTT, servidor, aplicativo e dashboard).
2. Como ocorre o fluxo de dados, desde a coleta do dado no ambiente até a visualização das informações pela gestão da fábrica.
3. Quais decisões ou ações poderiam ser tomadas com base nas informações exibidas no dashboard.
4. Quais são as vantagens de utilizar um sistema distribuído nesse contexto industrial.

## Análise:

A arquitetura proposta para o Projeto Integrador III reproduz, em escala didática, os princípios fundamentais do Sistema Digital de Controle Distribuído (SDCD) aplicados à automação de processos industriais. A distribuição do processamento entre dispositivos localizados próximos ao fenômeno físico monitorado, conectados a uma camada central de armazenamento e visualização, reflete a lógica que sustenta os sistemas distribuídos em plantas de grande porte, conforme descrito por Moraes e Castrucci (2007) ao tratarem das arquiteturas de controle distribuído na engenharia de automação.

### 1. Papel de cada componente

O **sensor de temperatura** atua como elemento de campo, responsável pela conversão de uma grandeza física em sinal mensurável. Posicionado diretamente no processo, representa o ponto de aquisição primária de dados, sem o qual nenhuma informação real estaria disponível para o restante da cadeia.

O **ESP32** desempenha função análoga a um controlador distribuído simplificado. Localizado próximo ao sensor, ele recebe o sinal, realiza conversão e filtragem inicial, e transmite os dados processados via rede. Sua proximidade ao ponto de medição reduz a necessidade de cabeamento extenso e confere autonomia de processamento local, característica central dos sistemas distribuídos, conforme observado por Groover (2011) ao descrever o paradigma da descentralização do controle em ambientes de manufatura.

O **protocolo MQTT** opera como meio de transporte das mensagens entre o controlador local e o servidor. Baseado no modelo publish/subscribe, permite comunicação assíncrona com baixo consumo de recursos, sendo indicado para aplicações de Internet das Coisas em contextos industriais, conforme apontado pela documentação técnica do protocolo mantida pela OASIS (2019).

O **servidor** corresponde à camada de processamento e persistência de dados. Recebe as mensagens publicadas, aplica lógica de armazenamento, e disponibiliza as informações para consumo pelas interfaces superiores. Na hierarquia do SDCD, equivale ao nível de supervisão e consolidação de dados.

O **aplicativo mobile** oferece acesso remoto às informações do processo, ampliando a mobilidade do operador ou gestor sem necessidade de presença física na sala de controle.

O **dashboard** consolida graficamente os dados coletados, apresentando indicadores, históricos e alertas. Funciona como interface supervisória equivalente ao SCADA nos sistemas industriais tradicionais, permitindo à gestão da fábrica uma visão consolidada do estado operacional da planta.

### 2. Fluxo de dados

O fluxo tem início no ambiente físico da fábrica, quando o sensor detecta a variação térmica do processo e gera um sinal correspondente. O ESP32 realiza a leitura periódica desse sinal, converte o dado em formato numérico e o publica em um tópico MQTT específico.

O broker MQTT encaminha a mensagem ao servidor, que a recebe, valida contra limites configurados e armazena em banco de dados. Os dados persistidos são então disponibilizados por meio de uma API para as interfaces de visualização.

O aplicativo mobile e o dashboard consomem essa API e renderizam as informações em formato gráfico, com indicadores em tempo real, séries históricas e alertas visuais. A gestão da fábrica acessa essas interfaces e obtém visibilidade do estado operacional sem a necessidade de inspecionar equipamentos individualmente.

### 3. Decisões a partir do dashboard

Com base nos dados consolidados no dashboard, diferentes ações podem ser desencadeadas pela equipe de gestão:

- **Controle de processo**: identificação de desvios de temperatura que exijam intervenção imediata, como acionamento de sistemas de resfriamento ou interrupção de uma etapa crítica.
- **Prevenção de falhas**: análise de tendências anormais que sinalizem degradação de equipamentos antes que ocorra parada não programada.
- **Monitoramento operacional**: acompanhamento contínuo das condições de operação das máquinas para validação de conformidade com parâmetros técnicos estabelecidos.
- **Gestão energética**: correlação entre variações térmicas e consumo energético para otimização de acionamentos.
- **Rastreabilidade**: registro automático de variáveis de processo para fins de auditoria, conformidade regulatória e certificações de qualidade.

### 4. Vantagens do sistema distribuído

A adoção de arquitetura distribuída no contexto do projeto apresenta vantagens estruturais relevantes:

- **Eliminação do ponto único de falha**: a falha de um ESP32 compromete apenas o trecho sob sua responsabilidade, mantendo o restante do sistema operacional. Diferentemente do modelo centralizado, onde a queda do controlador paralisava toda a planta, a distribuição isola os impactos.
- **Redução de cabeamento**: controladores posicionados junto aos sensores minimizam a extensão de cabos e os custos associados à infraestrutura física.
- **Escalabilidade**: novos sensores e controladores podem ser incorporados à rede sem reconfigurações estruturais do sistema existente, bastando a inclusão de novos dispositivos e tópicos de comunicação.
- **Processamento local**: o ESP32 pode executar lógica básica de controle, garantindo respostas imediatas a condições críticas mesmo diante de indisponibilidade momentânea da conexão de rede.
- **Visibilidade integrada**: o dashboard centraliza dados de múltiplos pontos de medição em uma interface unificada, oferecendo à gestão uma perspectiva abrangente da operação sem fragmentação de informações.
- **Manutenção facilitada**: a localização distribuída dos controladores simplifica a identificação e substituição de componentes com falha, reduzindo tempo de intervenção e impacto na produção.

## Referências

GROOVER, M. P. *Automação industrial e sistemas de manufatura*. São Paulo: Pearson, 2011.

MORAES, Cícero Couto de; CASTRUCCI, Plinio de Lauro. *Engenharia de automação industrial*. São Paulo: LTC, 2007.

OASIS. MQTT Version 5.0: OASIS Standard. OASIS Open, 2019. Disponível em: https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html. Acesso em: 20 mar. 2026.

LARA, Carla Eduarda Orlando de Moraes de. *Automação e controle industrial*. Curitiba: Contentus, 2021.

