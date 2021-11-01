## [Tópico T34a] - Projeto SISSA
###### *by Prof. Plinio Sa Leitao-Junior (INF/UFG)*

### Contexto

**Sissa** denota uma plataforma baseada em Inteligência Artificial que combina integração de dados acadêmicos, monitoramento eficiente de indicadores, previsão de sucesso do estudante, capacitação de tutores e interações por pares em um sistema que apoia o estudante.

Mais informações, favor clicar [aqui](https://sissa.ufg.br/).

### Integração de dados

Integração de dados se refere ao acesso, preferencialmente uniforme, a fontes de dados autônomas e heterogêneas. Noutras palavras, ter visão unificada dos dados de múltiplas fontes de dados díspares, internas e/ou externas. 

Algumas observações pertinenetes:
- O acesso aos dados (por exemplo, consultas) deve ocorrer de maneira uniforme (conteúdo e estrutura), mesmo no cenário de fontes heterogêneas:
  - também, deve haver independência em relação a alterações nas fontes de dados;
  - por exemplo, as fontes podem alterar seus formatos de dados e padrões de acesso a qualquer momento.
- Envolve fontes de dados que foram desenvolvidas independentemente umas das outras:
  - dados em bases relacionais, arquivos com conteúdo não estruturado, arquivos binários, arquivos JSON, arquivos XML, etc.
  - dados disponíveis por sistemas de gerencamento, por conexão/serviço Web, por acesso simples a um diretório, etc.
- O acesso aos dados podem requerer privacidade:
  - acesso restrito a usuários e a operações sobre os dados;
  - acesso apropriado no caso de dados sensíveis.
- O aumento do número de fontes representa um acréscimo importante aos desafios enfrentados.

### Estratégias de integração de dados:<br>Consolidação de dados _versus_ Virtualização de dados

1. **<ins>Consolidação de dados</ins>**<br>
É o processo clássico de integração de dados, que envolve a combinação de dados de fontes distintas, removendo suas redundâncias, eliminando quaisquer erros e agregando-os em um único armazenamento de dados, tal como um _data warehouse_.<br>
- Em geral, emprega uma abordagem do tipo ETL (_Extract_, _Transform_, _Load_):<br>
&#9745; **Extração**: Antes que os dados possam ser movidos para um novo destino, eles devem primeiro ser extraídos de sua origem. Dados estruturados e não estruturados são importados e consolidados em um único repositório. Nesta fase, os dados são chamados de 'dados brutos', e podem ser extraídos de uma ampla variedade de fontes.<br>
&#9745; **Transformação**: Regras podem ser aplicados para garantir a 'qualidade e acessibilidade' dos dados, e envolve:<br>
Limpeza - inconsistências e valores ausentes nos dados são resolvidos.<br>
Padronização - regras de formatação são aplicadas ao conjunto de dados.<br>
Deduplicação - dados redundantes são excluídos ou descartados.<br>
Verificação - dados inutilizáveis são removidos e anomalias são sinalizadas.<br>
Classificação - os dados são organizados de acordo com o tipo.<br>
Outras tarefas - quaisquer regras adicionais / opcionais podem ser aplicadas para melhorar a qualidade dos dados.<br>
- Os dados recém-transformados são então carregados em um novo destino (repositório). Os dados podem ser carregados todos de uma vez (carga total) ou em intervalos programados (carga incremental):<br>
&#9745; **Carregamento completo**: Todos os dados transformados (oriundos da linha de montagem de transformação) são carragedos como registros novos (e exclusivos) no _data warehouse_. Pode haver problemas de escala: manutenção dificultada pelo crescimento rápido (e exponencial) dos dados.<br>
&#9745; **Carregamento incremental**: Os dados recebidos são comparados com os dados disponíveis, e somente produz registros adicionais se informações novas e exclusivas forem encontradas.

2. **<ins>Virtualização de dados</ins>**<br>
Ao contrário das soluções ETL, que replicam dados, a virtualização de dados deixa os dados nos sistemas de origem, simplesmente expondo uma **visão integrada** de todos os dados aos consumidores de dados.<br>Alguns tipos comumente aplicados:
&#9745; **_Global as view_**: Conforme a figura a seguir, há um esquema global age como uma visão do esquema de origem, ou seja, o esquema do mediador é descrito em termos de esquema local. Dada uma consulta sobre o esquema global, o mediador seguirá as regras e modelos existentes para converter a consulta em consultas específicas da fonte. Ele envia as novas consultas aos wrappers para execução. O Wrapper procura todas as expressões possíveis e como elas podem ser combinadas para responder à consulta dada.



## Não há atividade para este tópico, excepcionalmente.