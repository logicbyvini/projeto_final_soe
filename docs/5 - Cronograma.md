### Cronograma Reestruturado do Projeto DMS

| **ID** | **Tarefa** | **Responsável** | **Predecessor** | **Data de Início** | **Data de Conclusão** | **% de Execução** | **Status** | **Prioridade** |
|:------:|------------|-----------------|:---------------:|:------------------:|:---------------------:|:-----------------:|:------------:|:--------------:|
| **1** | **Planejamento** | **Equipe** | - | **23/08/2026** | **01/10/2026** | **100%** | **Concluído** | **Alta** |
| 1.1 | Termo de Abertura do Projeto | Ambos | - | 23/08/2026 | 05/09/2026 | 100% | Concluído | Alta |
| 1.2 | Definição de Requisitos (RF e RNF) | Ambos | 1.1 | 06/09/2026 | 15/09/2026 | 100% | Concluído | Alta |
| 1.3 | Definição da Estrutura Analítica do Produto (EAP) | Gabriel | 1.2 | 16/09/2026 | 22/09/2026 | 100% | Concluído | Média |
| 1.4 | Definição do Projeto Conceitual (Software/Hardware) | Ambos | 1.2 | 16/09/2026 | 01/10/2026 | 100% | Concluído | Alta |
| 1.5 | Definição do Cronograma | Vinícius | 1.1 | 20/09/2026 | 01/10/2026 | 100% | Concluído | Alta |
| 1.6 | Definição do Orçamento | Gabriel | 1.3 | 20/09/2026 | 01/10/2026 | 100% | Concluído | Média |
| **2** | **Execução** | **Equipe** | **1** | **02/10/2026** | **04/12/2026** | **15%** | **Em andamento** | **Alta** |
| 2.1 | Aquisição de Partes e Componentes | Ambos | 1.6 | 23/08/2026 | 15/09/2026 | 100% | Concluído | Alta |
| 2.2 | Montagem e Codificação de Subsistemas | Ambos | 1.4, 2.1 | 02/10/2026 | 25/10/2026 | 0% | Em andamento | Alta |
| 2.2.1 | *Sub: Thread de Captura (V4L2) e Buffer Circular* | Vinícius | 1.4 | 02/10/2026 | 15/10/2026 | 0% | Não iniciado | Alta |
| 2.2.2 | *Sub: Thread de Processamento (EAR/Landmarks)* | Gabriel | 1.4 | 02/10/2026 | 20/10/2026 | 0% | Não iniciado | Alta |
| 2.2.3 | *Sub: Circuito Físico e Thread GPIO (libgpiod)* | Vinícius | 2.1 | 10/10/2026 | 22/10/2026 | 0% | Não iniciado | Média |
| 2.2.4 | *Sub: Thread de Telemetria e Sockets TCP* | Gabriel | 1.4 | 15/10/2026 | 25/10/2026 | 0% | Não iniciado | Média |
| 2.3 | Testes de Subsistemas (Testes Unitários) | Ambos | 2.2 | 26/10/2026 | 06/11/2026 | 0% | Não iniciado | Alta |
| 2.4 | Integração de Subsistemas (Pthreads + Mutex) | Ambos | 2.3 | 07/11/2026 | 18/11/2026 | 0% | Não iniciado | Alta |
| 2.5 | Testes de Integração e Latência (< 100 ms) | Ambos | 2.4 | 19/11/2026 | 28/11/2026 | 0% | Não iniciado | Alta |
| 2.6 | Apresentação Final do Produto | Ambos | 2.5, 3.9 | 29/11/2026 | 04/12/2026 | 0% | Não iniciado | Alta |
| **3** | **Documentação** | **Equipe** | - | **23/08/2026** | **04/12/2026** | **65%** | **Em andamento** | **Alta** |
| 3.1 | Documento: Termo de Abertura do Projeto | Ambos | 1.1 | 23/08/2026 | 05/09/2026 | 100% | Concluído | Alta |
| 3.2 | Documento: Requisitos de Sistema | Ambos | 1.2 | 06/09/2026 | 15/09/2026 | 100% | Concluído | Alta |
| 3.3 | Documento: Estrutura Analítica do Produto | Gabriel | 1.3 | 16/09/2026 | 22/09/2026 | 100% | Concluído | Média |
| 3.4 | Documento: Projeto Conceitual do Produto | Ambos | 1.4 | 16/09/2026 | 01/10/2026 | 100% | Concluído | Alta |
| 3.5 | Documento: Cronograma Detalhado | Vinícius | 1.5 | 20/09/2026 | 01/10/2026 | 100% | Concluído | Alta |
| 3.6 | Documento: Orçamento do Projeto | Gabriel | 1.6 | 20/09/2026 | 01/10/2026 | 100% | Concluído | Média |
| 3.7 | Documento: Plano e Relatório de Testes | Ambos | 2.5 | 19/11/2026 | 30/11/2026 | 0% | Não iniciado | Média |
| 3.8 | Documento: Avaliação de Desempenho (FPS/RAM) | Gabriel | 2.5 | 25/11/2026 | 02/12/2026 | 0% | Não iniciado | Alta |
| 3.9 | Documento: Relatório Final de Engenharia | Vinícius | 3.7, 3.8 | 25/11/2026 | 04/12/2026 | 0% | Não iniciado | Alta |

---
