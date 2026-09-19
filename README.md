# Metaindústria — Segurança Proativa com IA (Sprint 1)

## Integrantes

* Ana Clara Silveira Salvatico — 555389
* Eduardo Rodrigues Fernandes — 557219
* Emily Pereira Ribeiro — 554704
* Fernanda Pereira Molina Teixeira - 552587
* Vinicius Eiki Franca - 555150 

---

## Descrição

Sistema de visão computacional para monitoramento de segurança em ambientes industriais, capaz de:

* Detectar o uso correto de Equipamentos de Proteção Individual (EPIs)
* Identificar comportamentos de risco
* Analisar a postura dos operadores em tempo real

A solução gera **alertas proativos** e contribui para a **prevenção de acidentes**, alinhando-se aos princípios da **Indústria 4.0** e ao modelo de segurança **preventivo**.

---

## Problema

Nos ambientes industriais tradicionais:

* A segurança é majoritariamente reativa
* Há dificuldade no monitoramento contínuo do uso de EPIs
* Falta rastreabilidade de comportamentos de risco
* A identificação de não conformidades ocorre tardiamente

Isso resulta em aumento de acidentes, baixa eficiência na prevenção e dificuldade na tomada de decisão em tempo real.

---

## Objetivo

Desenvolver um sistema baseado em visão computacional capaz de monitorar ambientes industriais em tempo real, com foco em:

* Identificação automática do uso correto de EPIs
* Detecção de comportamentos de risco
* Análise de postura dos operadores

O sistema atua de forma **proativa**, gerando alertas imediatos diante de situações perigosas, com o objetivo de:

* Reduzir acidentes de trabalho
* Aumentar a segurança operacional
* Apoiar a tomada de decisão em tempo real

---

## Nossa Solução

A solução proposta consiste em um sistema inteligente de monitoramento de segurança que integra múltiplas técnicas de visão computacional:

* **Detecção de EPIs com YOLO**
* **Rastreamento de operadores em tempo real com ByteTrack**
* **Reconhecimento facial para identificação dos operadores**

Com base nessas informações, o sistema:

* Verifica se o operador está utilizando os EPIs obrigatórios
* Valida se o operador possui autorização/certificação para operar determinada máquina
* Monitora continuamente o comportamento em ambiente industrial

Caso alguma não conformidade seja identificada, o sistema pode:

* Emitir alertas em tempo real
* Registrar o evento de risco
* **Bloquear ou interromper a operação**, quando aplicável

Dessa forma, a solução atua de maneira **preventiva**, reduzindo riscos e promovendo um ambiente industrial mais seguro.

---

## Personas

### Operador

* Atua diretamente no chão de fábrica
* Pode esquecer ou utilizar incorretamente EPIs
* Precisa de alertas rápidos e objetivos

### Supervisor de Segurança

* Responsável por monitorar múltiplos operadores
* Atua na prevenção de riscos
* Necessita de visão em tempo real e histórico de eventos

### Administrador do Sistema

* Responsável pela configuração e manutenção do sistema.
* Define zonas de monitoramento no ambiente industrial.
* Associa máquinas às zonas configuradas.
* Configura os EPIs obrigatórios para cada máquina.
* Define as certificações necessárias para operação das máquinas.

---

## Escopo do Sistema

### Funcionalidades

* Detecção automática de EPIs
* Rastreamento de operadores
* Reconhecimento facial
* Emissão de alertas em tempo real
* Registro de eventos de risco
* Validação de certificação de operadores
* Bloqueio de operação em caso de não conformidade

### Restrições

* Dependência da qualidade das imagens
* Necessidade de processamento em tempo real
* Reconhecimento facial sujeito a limitações de precisão

---

## Tecnologias Utilizadas e Justificativas

### Backend / Processamento

- **Python**  
  Utilizado como linguagem principal no processamento de imagens e integração com modelos de Inteligência Artificial, devido à ampla compatibilidade com bibliotecas de visão computacional e Machine Learning.

- **OpenCV**  
  Responsável pela manipulação de imagens e vídeos em tempo real, permitindo captura, leitura, processamento de frames e integração com os modelos de detecção.


### Inteligência Artificial

- **YOLO (You Only Look Once)**  
  Utilizado para detecção de EPIs em tempo real devido à sua alta velocidade e precisão em tarefas de visão computacional, sendo adequado para aplicações industriais que exigem baixa latência.

- **ByteTrack**  
  Utilizado para rastreamento de múltiplos operadores no ambiente industrial, permitindo manter a identificação contínua dos indivíduos durante o monitoramento.


### Ferramentas

- **Google Colab**  
  Utilizado para treinamento, testes e validação dos modelos de IA, aproveitando recursos computacionais em nuvem e aceleração por GPU.

- **Makesense.ai**  
  Utilizado na anotação das imagens para treinamento dos modelos de visão computacional, permitindo criação de datasets personalizados para detecção de EPIs.


### Banco de Dados

- **PostgreSQL**  
  Utilizado para armazenamento de eventos, registros de monitoramento, alertas e informações relacionadas às validações realizadas pelo sistema, devido à sua confiabilidade, escalabilidade e suporte a dados relacionais.


### Backend Complementar

- **Java**  
  Utilizado para implementação das regras de negócio e integração entre os componentes do sistema, oferecendo robustez, organização arquitetural e facilidade de manutenção em aplicações corporativas.
---

## Requisitos

**Fonte dos requisitos:** levantamento baseado na apresentação oficial da empresa no contexto do Challenge 2026 (FIAP × SPI Integração), complementado por análise do problema e definição das funcionalidades da solução proposta.

### Requisitos Funcionais

Os requisitos funcionais descrevem as funcionalidades que o sistema deve executar.

- **RF01 – Detectar pessoas em tempo real**  
  O sistema deve identificar indivíduos no ambiente por meio de vídeo.

- **RF02 – Detectar Equipamentos de Proteção Individual (EPIs)**  
  O sistema deve detectar EPIs como capacete, colete, luvas e outros configurados.

- **RF03 – Rastrear operadores ao longo do tempo**  
  O sistema deve manter a identificação de cada indivíduo por meio de tracking (Track ID).

- **RF04 – Identificar operadores**  
  O sistema deve reconhecer o operador utilizando reconhecimento facial.

- **RF05 – Identificar zona de monitoramento**  
  O sistema deve identificar em qual zona o operador está localizado.

- **RF06 – Associar operador à máquina**  
  O sistema deve relacionar o operador detectado à máquina presente na zona monitorada.

- **RF07 – Validar certificações do operador**  
  O sistema deve verificar se o operador possui as certificações necessárias para operar a máquina identificada.

- **RF08 – Validar uso de EPIs por operador**  
  O sistema deve verificar se o operador está utilizando todos os EPIs obrigatórios definidos para a máquina associada.

- **RF09 – Controlar operação da máquina**  
  O sistema deve permitir, bloquear ou interromper a operação da máquina com base nas validações realizadas.

- **RF10 – Emitir alertas de risco**  
  O sistema deve gerar alertas em tempo real ao identificar não conformidades.

- **RF11 – Registrar eventos**  
  O sistema deve registrar eventos relevantes (ex: tentativa de uso sem EPI, bloqueios, desligamentos).

- **RF12 – Operar em tempo real**  
  O sistema deve processar os dados continuamente, permitindo tomada de decisão imediata.

- **RF13 – Definir zonas de monitoramento**  
  O sistema deve permitir ao administrador cadastrar e gerenciar zonas de monitoramento.

- **RF14 – Associar máquinas às zonas**  
  O sistema deve permitir associar máquinas a zonas específicas.

- **RF15 – Definir EPIs obrigatórios por máquina**  
  O sistema deve permitir configurar os EPIs exigidos para cada máquina.

- **RF16 – Definir certificações por máquina**  
  O sistema deve permitir configurar as certificações necessárias para operação de cada máquina.

### Requisitos Não Funcionais

Os requisitos não funcionais descrevem as características de qualidade do sistema.

### Requisitos Não Funcionais (RNF)

- **RNF01 – Desempenho em tempo real**  
  O sistema deve apresentar baixa latência entre captura e decisão.

- **RNF02 – Precisão**  
  O sistema deve atingir níveis adequados de precisão na detecção de pessoas e EPIs.

- **RNF03 – Robustez**  
  O sistema deve funcionar adequadamente sob variações de iluminação, oclusões e diferentes condições do ambiente.

- **RNF04 – Escalabilidade**  
  O sistema deve permitir expansão para múltiplas câmeras, zonas e máquinas.

- **RNF05 – Confiabilidade**  
  O sistema deve minimizar falhas que possam gerar bloqueios ou liberações indevidas.

- **RNF06 – Manutenibilidade**  
  O sistema deve permitir atualização de modelos e regras sem necessidade de grandes alterações estruturais.

- **RNF07 – Eficiência computacional**  
  O sistema deve ser capaz de operar em ambientes com recursos limitados (ex: edge devices).
---

## Documentação do Projeto

Os diagramas UML e documentos da Sprint 1 estão disponíveis diretamente na raiz principal do repositório GitHub.

### Diagramas UML

- Diagrama de Casos de Uso  
- Diagrama de Atividades  
- Diagrama de Classes  

### Documento de Requisitos

- Documento contendo os requisitos funcionais e não funcionais do sistema.

> Todos os arquivos podem ser acessados diretamente pela página principal do repositório.

## Protótipo Navegável (Sprint 2)

O protótipo de alta fidelidade do sistema **Lazuli — Controle Industrial** está disponível no Figma:

🔗 **Link do protótipo:** [[Figma](https://www.figma.com/design/1MUdcD5Y0e2eWfxA42v2DO/Projeto-SPI?node-id=0-1&t=geIx5mIYYFMS3Q9U-1)] (permissão de visualização ativa)

📄 **Documentação de design** (mapa de telas, decisões de UX e mapeamento com os casos de uso da Sprint 1): [`documentacao-design-lazuli.md`](documentacao-design-lazuli.md)

🎥 **Vídeo de walkthrough:** [Link do video](https://youtu.be/DzM2R6Macwo)

### Como navegar pelo protótipo

1. **Login** — Tela inicial de acesso ao sistema (ID e senha).
2. **Dashboard** — Visão geral de conformidade, riscos críticos ativos e feeds das câmeras. A partir daqui, clique em:
   - **"Verificar"** no alerta da CAM-04 para abrir a tela de detalhe da câmera e visualizar o alerta de invasão de zona em tempo real.
3. **Operadores** — Acesse pela barra lateral para consultar a lista de operadores e seus status de certificação. Clique em **"Novo Operador"** para simular o cadastro de EPIs e certificações NR de um colaborador.
4. **Câmeras** — Lista de câmeras monitoradas. Clique na primeira câmera(REC • CH-01) para ver telemetria e entidades detectadas, ou em **"Configurar Marcações"** para simular a definição de zonas de risco.
5. **Máquinas** — Inventário de ativos com requisitos de EPI vinculados a cada máquina.
6. **Relatórios** — Acesse o painel de conformidade por setor, filtre por setor (ex: Fundição) e visualize o benchmark e os registros de não conformidade. Use o botão **"Exportar PDF"** para simular a geração do relatório.
7. **Configurações** — Tela administrativa para gerenciamento de usuários e integrações do sistema.

> 💡 Recomenda-se iniciar a navegação pela tela de **Login** para seguir o fluxo completo conforme apresentado no vídeo de walkthrough.

---

## Atualizações Sprint 3

### Novas telas

Foram adicionadas duas novas telas ao protótipo nesta sprint, ligadas ao fluxo de liberação de acesso a uma máquina:

**Cadastro Facial** — tela onde a referência facial do operador é capturada e registrada no sistema (durante o cadastro do operador ou em uma atualização posterior). Essa referência é a base usada para o reconhecimento automático do operador.
**Check-in** — tela acionada antes do operador iniciar o uso de uma máquina. O operador é identificado por reconhecimento facial em tempo real, comparando a captura da câmera com a referência salva no Cadastro Facial. Após a confirmação da identidade, exibe as certificações e os EPIs exigidos para aquela máquina antes de liberar o acesso. Em caso de falha no reconhecimento, é oferecido um caminho alternativo de identificação (ID/crachá).

## Protótipo (Figma)
[[Figma](https://www.figma.com/design/1MUdcD5Y0e2eWfxA42v2DO/Projeto-SPI?node-id=0-1&t=geIx5mIYYFMS3Q9U-1)] (permissão de visualização ativa)

## Impacto na arquitetura

Essas mudanças não representaram alterações na arquitetura técnica da aplicação. O reconhecimento facial já estava previsto desde as etapas anteriores do projeto — apenas não havia sido desenvolvido/prototipado ainda. Nesta sprint, essa funcionalidade foi de fato implementada no protótipo, junto com o fluxo de check-in que a utiliza.

