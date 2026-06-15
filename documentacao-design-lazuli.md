# Documentação de Design — Lazuli (Controle Industrial)

> **Sprint 2 — Prototipação Funcional e Navegável da Solução**
> Este documento descreve o mapa de telas, as decisões de UX/UI e o mapeamento entre as telas do protótipo e os casos de uso definidos na Sprint 1.

---

## 1. Mapa de Telas

```
[Login]
   |
   v
[Dashboard] --- [Câmeras (lista)] --- [Câmera Detalhe / Telemetria] --- [Configurar Marcações de Zona]
   |                                          |
   |                                          v
   |                                  [Cadastro de Câmera]
   |
   |--- [Máquinas (lista)] --- [Cadastro de Nova Máquina]
   |
   |--- [Operadores (lista)] --- [Cadastro de Novo Operador]
   |
   |--- [Relatórios de Conformidade]
   |
   |--- [Configurações Gerais]
```

### Descrição das telas

| Tela | Descrição resumida |
|---|---|
| Login | Tela de autenticação com ID e senha, fundo com imagem do ambiente industrial |
| Dashboard | Visão geral em tempo real: conformidade global, riscos críticos, feeds ativos das câmeras e fluxo de eventos |
| Câmeras (lista) | Listagem de todas as câmeras com status (online/offline), alertas de EPI e máquinas monitoradas |
| Câmera Detalhe | Visualização ao vivo de uma câmera específica, com telemetria, entidades detectadas e status de zonas |
| Configurar Marcações de Zona | Definição de polígonos de zonas de risco/máquina sobre o feed da câmera |
| Cadastro de Câmera | Formulário de cadastro de nova câmera/sensor, parâmetros de streaming e zonas de análise |
| Máquinas (lista) | Inventário de ativos com status operacional, zona/câmera vinculada e requisitos de EPI |
| Cadastro de Nova Máquina | Formulário de cadastro de ativo, com checklist de EPIs obrigatórios |
| Operadores (lista) | Gestão de operadores: certificações ativas, status de autorização de acesso |
| Cadastro de Novo Operador | Formulário de cadastro de operador com certificações NR e controle de acesso físico |
| Relatórios de Conformidade | Painel com KPIs, benchmark de conformidade por setor e registros de não conformidade |
| Configurações Gerais | Gerenciamento de usuários administradores, integrações e preferências de interface |

---

## 2. Decisões de UX/UI

| Decisão | Justificativa | Persona relacionada |
|---|---|---|
| Tema dark mode em toda a aplicação | Reduz fadiga visual em ambientes de baixa luminosidade (chão de fábrica, salas de controle) e aumenta o contraste de alertas críticos | Operador de Sala de Controle |
| Modo "Operação Noturna" (alto contraste) | Garante legibilidade em turnos noturnos e em telas expostas a reflexo de luz industrial | Operador de Turno Noturno |
| Cores de status padronizadas (vermelho = crítico, roxo = ação primária, verde/azul = ok) | Permite leitura rápida de alertas sem necessidade de leitura textual — crítico para decisões em segundos | Gestor de Segurança / Operador de Campo |
| Cards de KPI no topo de cada tela | Fornece visão geral imediata antes dos detalhes, atendendo à necessidade de checagem rápida no início do turno | Gestor de Setor |
| Sidebar fixa com ícones + labels | Facilita a navegação consistente entre módulos e reduz a curva de aprendizado | Todos os perfis |
| Checklist de EPIs com ícones e descrições | Reduz erros de cadastro e orienta operadores menos familiarizados com nomenclatura técnica | Técnico de Segurança do Trabalho |
| Botões de ação primária sempre em roxo (#7c5cff) | Cria consistência visual e direciona o olhar para a ação mais importante de cada tela | Todos os perfis |
| Badges de status (Operacional, Crítico, Bloqueado, etc.) | Comunica estado de forma compacta e visualmente escaneável em listas longas | Gestor de Setor / Operador de Campo |
| Layout responsivo pensado para tablets industriais | Telas com cards grandes e áreas de toque amplas, adequadas para uso com luvas em campo | Operador de Campo |

---

## 3. Mapeamento Telas × Casos de Uso (Sprint 1)

Com base no Diagrama de Casos de Uso "Sistema de monitoramento de segurança industrial" (Sprint 1), que define dois atores principais — **Supervisor de Segurança** e **Administrador do Sistema** — e três pacotes automáticos (Monitoramento, Validação e Ação do Sistema).

### 3.1 Atores e seus casos de uso

| Ator | Casos de Uso (Sprint 1) |
|---|---|
| Supervisor de Segurança | Visualizar monitoramento, Receber alertas, Consultar eventos registrados |
| Administrador do Sistema | Configurar câmeras, Definir zonas de monitoramento, Associar máquinas à zona, Definir certificações obrigatórias por máquina, Definir EPIs obrigatórios por máquina |
| Sistema (automático) | Monitorar ambiente industrial, Detectar pessoas, Detectar EPIs, Rastrear operadores, Validar operador, Validar uso de EPIs, Validar certificação do operador, Verificar conformidade, Emitir alerta, Controlar operação da máquina, Registrar evento |

### 3.2 Mapeamento detalhado

| Tela | Caso(s) de Uso (Sprint 1) | Descrição do fluxo coberto |
|---|---|---|
| Login | *(pré-condição transversal — autenticação dos atores Supervisor e Administrador)* | Acesso via ID e senha |
| Dashboard | Visualizar monitoramento; Receber alertas; Verificar conformidade | Visão geral de conformidade global, riscos críticos ativos, feeds das câmeras e fluxo de eventos em tempo real |
| Câmeras (lista) | Configurar câmeras; Monitorar ambiente industrial | Listagem de câmeras com status online/offline e alertas de EPI vinculados ao monitoramento automático |
| Câmera Detalhe (CAM-04) | Detectar pessoas; Detectar EPIs; Rastrear operadores; Emitir alerta | Visualização ao vivo com entidades detectadas (operador, empilhadeira, desconhecido) e status de invasão de zona |
| Configurar Marcações de Zona | Definir zonas de monitoramento; Associar máquinas à zona | Desenho de polígonos de zonas de risco/máquina e vínculo com ativos cadastrados |
| Cadastro de Câmera | Configurar câmeras | Cadastro de nova câmera/sensor, definição de URL RTSP, resolução, FPS e zonas de análise |
| Máquinas (lista) | Associar máquinas à zona; Controlar operação da máquina | Inventário de ativos com status operacional, zona/câmera vinculada e ações de controle |
| Cadastro de Nova Máquina | Definir EPIs obrigatórios por máquina; Definir certificações obrigatórias por máquina | Cadastro de ativo com checklist de EPIs obrigatórios para a IA monitorar |
| Operadores (lista) | Validar operador; Validar certificação do operador; Validar uso de EPIs | Gestão de operadores com status de autorização (Autorizado/Bloqueado) com base em certificações |
| Cadastro de Novo Operador | Validar certificação do operador; Validar uso de EPIs | Cadastro de operador com certificações NR obrigatórias e controle de acesso físico por zona |
| Relatórios de Conformidade | Consultar eventos registrados; Verificar conformidade; Registrar evento | Painel com benchmark de conformidade por setor, registros de não conformidade e exportação |
| Configurações Gerais | Configurar câmeras *(parte administrativa)* | Gerenciamento de usuários administradores, integrações e preferências de interface |

### 3.3 Casos de uso ainda sem tela dedicada (avaliar na próxima sprint)

- **Detectar pessoas / Detectar EPIs / Rastrear operadores**: hoje representados como resultado dentro da tela de Câmera Detalhe, mas não há uma tela que exponha esse processamento de forma independente (pode ser aceitável, já que são automáticos e "invisíveis" ao usuário)
- **Controlar operação da máquina**: aparece como conceito na lista de Máquinas, mas não há uma ação explícita (ex: botão "Pausar/Parar máquina") — vale avaliar se isso precisa de um modal ou ação na tela de detalhe da máquina

---

## 4. Fluxos Principais Demonstrados (para o vídeo de walkthrough)

### Fluxo 1 — Cadastro e consulta de EPI por colaborador
1. Acessar **Operadores** (lista)
2. Clicar em **Novo Operador**
3. Preencher dados pessoais e anexar certificações NR obrigatórias (NR-12, NR-35, NR-10, NR-33)
4. Configurar o controle de acesso físico (zonas liberadas)
5. Salvar registro
6. Voltar à lista de Operadores e verificar status "Autorizado"

### Fluxo 2 — Emissão e visualização de alerta de risco
1. No **Dashboard**, observar o card "Riscos Críticos Ativos" e o alerta na CAM-04 (Zona de Carga B)
2. Clicar em **Verificar**
3. Ser direcionado à tela de **Câmera Detalhe (CAM-04)**
4. Visualizar a entidade "#UK-001 — Desconhecido" com status "INVASÃO" na Zona de Risco C
5. (Opcional) Acessar **Configurar Marcações** para mostrar como a zona de risco foi definida

### Fluxo 3 — Geração de relatório de conformidade por setor
1. Acessar **Relatórios de Conformidade**
2. Filtrar por setor (ex: Fundição)
3. Analisar o gráfico de **Benchmarks de Conformidade**
4. Consultar a tabela de **Registros de Não Conformidade**
5. Clicar em **Exportar PDF**

---

## 5. Considerações para Contexto de Campo (Diferencial)

- **Tablet industrial**: cards e botões com áreas de toque ampliadas, adequados ao uso com luvas
- **Leitura rápida de alertas**: uso consistente de cores (vermelho/laranja) e badges para que decisões críticas não dependam de leitura detalhada de texto
- **Modo Operação Noturna**: contraste reforçado para uso em ambientes com pouca luz ou alta exposição a reflexos
- **Hierarquia visual**: informações mais críticas (riscos, não conformidades) sempre posicionadas no topo das telas, seguindo o padrão F de leitura

---

## 6. Próximos Passos

- [ ] Garantir navegação real (cliques funcionais) entre todas as telas no Figma
- [ ] Avaliar inclusão de tela/ação para "Controlar operação da máquina" (item 3.3)
- [ ] Atualizar README do repositório com link do protótipo e instruções de navegação
- [ ] Gravar vídeo de walkthrough (até 3 min) cobrindo os 3 fluxos principais
- [ ] Preencher arquivo final `.txt` com nomes, RMs, links de GitHub, Figma e YouTube
