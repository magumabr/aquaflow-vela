# ⛵ AquaFlow — Sistema Integrado para Gestão de Escolas de Vela e Esportes Aquáticos

> **Projeto Integrador | Engenharia de Computação — CEUB**  
> **Professor:** Uender Amaral  
> **Autor:** [Seu Nome Aqui]  
> **Repositório oficial de acompanhamento (Book & MVP)**

---

## 📌 1. Contexto e Definição do Problema Real

A gestão de escolas de esportes infantis e aquáticos — como a Escola de Vela do Iate Clube de Brasília — lida com uma rotina operacional altamente dinâmica, dependente de condições climáticas (vento, chuva) e de forte acompanhamento dos pais. 

Atualmente, o fluxo operacional é mantido de forma manual através de planilhas de Excel (`CHAMADA 2026.xlsx` e `Programação 2026 27.xlsx`) e disparo de mensagens em grupos não estruturados de WhatsApp.

### Dores Identificadas por Perfil:

1. **Gestão / Coordenação:**
   * Gasto excessivo de horas montando calendários e planilhas manualmente célula por célula.
   * Risco constante de perda de dados históricos ou corrupção de arquivos Excel.
   * Dificuldade de consolidar alertas prévios de aulas e avisos de condições climáticas para os pais.

2. **Corpo Docente (Professores/Instrutores de Cais):**
   * Dificuldade e lentidão para realizar chamadas no cais ou beira do lago via smartphone em planilhas extensas (com centenas de colunas).
   * Erros acidentais de digitação que apagam fórmulas e dados de alunos.
   * Impossibilidade de registrar notas de comportamento (escala 0 a 3) e observações pedagógicas/médicas em tempo real.

3. **Alunos e Responsáveis (Pais):**
   * Falta de um canal centralizado para visualizar presenças, calendários atualizados e avisos prévios de aula.
   * Dificuldade para acompanhar o progresso dos filhos e acessar fotos/vídeos em alta resolução com segurança.

---

## 🎯 2. Hipóteses e Métricas de Sucesso

* **Hipótese Principal:** A substituição de planilhas descentralizadas por um ambiente web com perfil por papel (Gestor, Professor, Pais) reduzirá o tempo de registro de chamadas e eliminará erros de perda de dados.
* **Métrica Mensurável (Sinal):** 
  * Redução do tempo médio de registro da chamada de **5 minutos (no papel/Excel)** para **menos de 45 segundos** por turma via interface web.
  * Preservação integral dos dados no banco relacional (SQLite/PostgreSQL) com zero perda de registros.

---

## 👥 3. Histórias de Usuário (User Stories)

### 3.1. História do Gestor (Coordenação)
> **Como** Coordenador da Escola de Vela,  
> **Quero** automatizar a geração do calendário anual e a consolidar as chamadas em um sistema centralizado,  
> **Para que** eu não precise criar planilhas manuais no Excel nem gastar horas notificando pais em grupos de WhatsApp.

* **Critérios de Aceite:**
  * O sistema deve permitir o cadastro de turmas, alunos e programação de aulas sem uso de tabelas externas.
  * O gestor deve conseguir visualizar relatórios sintéticos de frequência por turma e por aluno com um clique.

### 3.2. História do Professor (Instrutores)
> **Como** Instrutor de Vela da Iniciação,  
> **Quero** uma interface mobile de chamada simples onde eu possa marcar presenças, atribuir nota de comportamento (0 a 3) e adicionar observações,  
> **Para que** eu não corra o risco de apagar dados da planilha original e possa finalizar a chamada rapidamente direto do cais.

* **Critérios de Aceite:**
  * A chamada deve ser realizada exibindo apenas a lista da turma selecionada para o dia.
  * A interface deve conter seletores rápidos para Presença/Falta, uma escala de comportamento (0, 1, 2, 3) e um campo de observações.
  * O sistema deve impedir que o professor altere dados estruturais de cadastros ou outras turmas.

### 3.3. História dos Pais / Responsáveis
> **Como** Pai/Mãe de um aluno da iniciação,  
> **Quero** acessar um painel onde possa visualizar a presença do meu filho, receber lembretes das aulas com 1 dia de antecedência e baixar mídias (fotos/vídeos) em alta qualidade,  
> **Para que** eu acompanhe a evolução do meu filho e não perca compromissos ou alertas importantes.

* **Critérios de Aceite:**
  * O responsável deve visualizar o histórico de frequência do seu filho em forma de calendário.
  * O portal deve fornecer links/galeria seguros para download de mídias das velejadas.

---

## 📋 4. Mapeamento do Backlog (MVP Acadêmico vs. Expansão Comercial)

Para atender ao rigor acadêmico do Projeto Integrador (foco em entrega ponta a ponta reproduzível), o projeto foi dividido em duas fases:

```
+-------------------------------------------------------------------+
|                     ESCOPO DO PROJETO (BACKLOG)                   |
+-------------------------------------------------------------------+
| [X] MVP ACADÊMICO (Disciplinas CEUB)                              |
|     └── Autenticação de Usuários (Login)                          |
|     └── Visualização de Turmas do Dia                             |
|     └── Registro de Frequência, Comportamento (0-3) e Observação  |
|     └── Persistência no Banco de Dados (SQLite + SQLAlchemy)      |
|     └── Testes Automatizados (pytest) + Tratamento OWASP        |
|                                                                   |
| [ ] EXPANSÃO COMERCIAL (Versão Futura / Produto Comercial)        |
|     └── Dashboard Financeiro & Cobrança Automática (PIX/Cartão)   |
|     └── Galeria de Fotos/Vídeos HD com AWS S3                     |
|     └── Disparo de Alertas Climáticos via WhatsApp API / Push     |
|     └── Gamificação Completa (Sistema de Conquistas e Nós)        |
+-------------------------------------------------------------------+
```

---

## 🛠️ 5. Arquitetura e Stack Tecnológica (MVP)

A arquitetura segue o modelo em camadas com rotas REST e persistência relacional:

* **Front-end:** HTML5 Semantic, CSS3 (Tailwind/CSS nativo) e JavaScript Vanilla (DOM API + Fetch API).
* **Back-end:** Python 3.11+ com framework **FastAPI** (Documentação automática OpenAPI/Swagger).
* **Persistência de Dados:** SQLite3 gerenciado via **SQLAlchemy ORM**.
* **Qualidade e Testes:** `pytest` para testes unitários e de integração de rotas.
* **Containers & Reprodutibilidade:** Docker & Docker Compose.

---

## 🚦 6. Definition of Done (DoD) — Critério de Conclusão

Uma funcionalidade é considerada **Done (Pronta)** apenas quando atende aos seguintes requisitos:

1. O código-fonte está commitado no repositório GitHub com mensagens claras.
2. A rota da API REST `/api/v1` possui cobertura de testes verdes via `pytest`.
3. A interface web consegue ler e gravar dados persistidos no SQLite sem perda após reinício da aplicação.
4. O ambiente roda localmente via Docker sem erros de dependência.

---

## 🚀 7. Guia de Execução Local (Reprodutibilidade)

### Pré-requisitos
* Python 3.11+ instalado ou Docker Desktop.

### Passos para Rodar Localmente (sem Docker)

1. **Clonar o repositório:**
   ```bash
   git clone https://github.com/SEU-USUARIO/aquaflow-vela.git
   cd aquaflow-vela
   ```

2. **Criar e ativar o ambiente virtual:**
   ```bash
   python -m venv venv
   # No Windows:
   venv\Scripts\activate
   # No Linux/Mac:
   source venv/bin/activate
   ```

3. **Instalar dependências:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Executar o servidor FastAPI:**
   ```bash
   uvicorn app.main:app --reload
   ```

5. **Acessar no navegador:**
   * Interface Web: `http://localhost:8000`
   * Documentação da API (Swagger): `http://localhost:8000/docs`

---
*Projeto sob licença acadêmica CEUB — 2026/2.*