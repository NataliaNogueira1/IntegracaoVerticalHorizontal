# 📚 Resumo da aula

**Prof. Me. Deivison S. Takatu**

**Data: 20/03/2026**

**Tema da aula: Sistemas Digital de Controle Distribuído**

---

## Tópicos abordados

- Conceituação do Sistema Digital de Controle Distribuído (SDCD)
- Limitações do modelo centralizado de controle
- Componentes e funcionamento do SDCD
- Vantagens da distribuição do controle na planta industrial
- Estudo de caso da TSMC

## Sistema Digital de Controle Distribuído (SDCD)

- Surgiu para superar as fragilidades do controle centralizado, no qual a falha de um único equipamento comprometia toda a operação
- Distribui o processamento entre múltiplos controladores posicionados próximos aos equipamentos que monitoram
- Cada controlador é responsável por uma etapa específica do processo produtivo
  ![alt text](image.png)
- A comunicação entre os controladores ocorre por meio de redes industriais dedicadas
- Uma estação de supervisão centraliza a visualização dos dados, mas não concentra o controle

## Vantagens observadas

- Eliminação do ponto único de falha
- Redução significativa de cabeamento
- Redundância: outro controlador assume em caso de falha
- Alta disponibilidade e adequação a processos contínuos
- Escalabilidade para inclusão de novos pontos de controle

## Estudo de caso - TSMC

- A TSMC opera com processos que não podem ser interrompidos
- Utiliza arquitetura distribuída para garantir continuidade operacional
- A planta nunca para completamente, mesmo durante manutenções

