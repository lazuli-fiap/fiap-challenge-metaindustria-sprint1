# Metaindústria — Segurança Proativa com IA (Sprint 1)

## Integrantes

* Ana Clara Silveira Salvatico — 555389
* Eduardo Rodrigues Fernandes — 557219
* Emily Pereira Ribeiro — 557219
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

---

## Escopo do Sistema

### Funcionalidades

* Detecção automática de EPIs
* Rastreamento de operadores
* Reconhecimento facial
* Emissão de alertas em tempo real
* Registro de eventos de risco
* Validação de certificação de operadores
* Possível bloqueio de operação em caso de não conformidade

### Restrições

* Dependência da qualidade das imagens
* Necessidade de processamento em tempo real

---

## Stack Utilizada

### Backend / Processamento

* **Python** → processamento de imagens e integração com IA
* **OpenCV** → manipulação de vídeo e imagens

### Inteligência Artificial

* **YOLO** → detecção de EPIs em tempo real
* **ByteTrack** → rastreamento de múltiplos operadores

### Ferramentas

* **Google Colab** → treinamento e testes dos modelos
* **Makesense.ai** → anotação de imagens

### Dados

* **PostgreSQL** → armazenamento de eventos e registros

### Backend complementar

* **Java** → regras de negócio e integração de sistema

---

## Requisitos

**Fonte dos requisitos:** levantamento baseado na apresentação oficial da empresa no contexto do Challenge 2026 (FIAP × SPI Integração), complementado por análise do problema e definição das funcionalidades da solução proposta.

### Requisitos Funcionais

Os requisitos funcionais descrevem as funcionalidades que o sistema deve executar.

* **RF01 – Detectar pessoas em tempo real**
  O sistema deve identificar indivíduos no ambiente por meio de vídeo.
* **RF02 – Detectar Equipamentos de Proteção Individual (EPIs)**
  O sistema deve detectar EPIs como capacete, colete, luvas e outros configurados.
* **RF03 – Rastrear operadores ao longo do tempo**
  O sistema deve manter a identificação de cada indivíduo por meio de tracking (Track ID).
* **RF04 – Identificar operadores**
  O sistema deve reconhecer o operador utilizando reconhecimento facial.
* **RF05 – Validar certificações do operador**
  O sistema deve verificar se o operador possui as certificações necessárias para operar determinada máquina.
* **RF06 – Validar uso de EPIs por operador**
  O sistema deve verificar se o operador está utilizando todos os EPIs obrigatórios definidos para a máquina.
* **RF07 – Associar operador à máquina**
  O sistema deve relacionar o operador detectado à máquina monitorada.
* **RF08 – Controlar operação da máquina**
  O sistema deve permitir, bloquear ou interromper a operação da máquina com base nas validações realizadas.
* **RF09 – Operar em tempo real**
  O sistema deve processar os dados continuamente, permitindo tomada de decisão imediata.
* **RF10 – Registrar eventos**
  O sistema deve registrar eventos relevantes (ex: tentativa de uso sem EPI, bloqueios, desligamentos).

### Requisitos Não Funcionais

Os requisitos não funcionais descrevem as características de qualidade do sistema.

* **RNF01 – Desempenho em tempo real**
  O sistema deve apresentar baixa latência entre captura e decisão.
* **RNF02 – Precisão**
  O sistema deve atingir níveis adequados de precisão na detecção de pessoas e EPIs.
* **RNF03 – Robustez**
  O sistema deve funcionar adequadamente sob variações de iluminação, oclusões e diferentes condições do ambiente.
* **RNF04 – Escalabilidade**
  O sistema deve permitir expansão para múltiplas câmeras e máquinas.
* **RNF05 – Confiabilidade**
  O sistema deve minimizar falhas que possam gerar bloqueios ou liberações indevidas.
* **RNF06 – Manutenibilidade**
  O sistema deve permitir atualização de modelos e regras sem necessidade de grandes alterações estruturais.
* **RNF07 – Eficiência computacional**
  O sistema deve ser capaz de operar em ambientes com recursos limitados (ex: edge devices).

---

## Modelagem UML

### Diagrama de Casos de Uso

Local: `/docs/uml/casos_de_uso.png`

### Diagrama de Atividades

Local: `/docs/uml/atividade.png`

### Diagrama de Classes

Local: `/docs/uml/classes.png`

---

