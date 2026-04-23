**Dupla:** Guilherme Siqueira + 227421 | Patrick Santos + 225469
**Data da exploração:** 23/04/2026
**Navegador usado:** Chrome 121
**Sistema operacional:** Windows 10

---



## BUG-01

**Título:** [VALIDAÇÃO] Sistema permite criar tarefa sem título

**Severidade:** Média
**Justificativa da severidade:** Permite cadastro de dados inválidos, prejudicando a usabilidade e organização das tarefas.

**Prioridade:** P2
**Justificativa da prioridade:** Afeta a qualidade dos dados, mas não impede o funcionamento do sistema.

**Ambiente:**
- Navegador: Chrome 121.0
- Sistema Operacional: Windows 11
- Versão da aplicação: TarefaQS v1.0.0

**Passos para reprodução:**
1. Acessar o sistema
2. Deixar o campo "título" vazio
3. Preencher os outros campos (ou não)
4. Clicar em "Adicionar tarefa"

**Resultado esperado:**
O sistema deveria impedir a criação da tarefa e exibir uma mensagem de erro.

**Resultado obtido:**
A tarefa é criada mesmo sem título.

**Evidência:**
js
const titulo = inputTitulo.value.trim();
// Não há validação antes de criar a tarefa

---

## BUG-02

**Título:** [LÓGICA] Contagem de tarefas pendentes está incorreta (duplicação de tarefas urgentes)

**Severidade:** Média
**Justificativa da severidade:** O sistema apresenta dados incorretos ao usuário, impactando a confiabilidade das informações exibidas.

**Prioridade:** P2
**Justificativa da prioridade:** Não impede o uso, mas compromete a precisão das estatísticas.

**Ambiente:**
- Navegador: Chrome 121.0
- Sistema Operacional: Windows 11
- Versão da aplicação: TarefaQS v1.0.0

**Passos para reprodução:**
1. Criar uma tarefa com prioridade 5
2. Garantir que ela não esteja concluída
3. Observar o contador de tarefas pendentes

**Resultado esperado:**
A tarefa deveria ser contabilizada apenas uma vez como pendente.

**Resultado obtido:**
A tarefa é contabilizada duas vezes, pois tarefas urgentes são somadas novamente.

**Evidência:**
js
let pendentes = tarefas.filter(function(t) { return !t.concluida; }).length;

const urgentes = tarefas.filter(function(t) {
  return t.prioridade === 5 && !t.concluida;
}).length;

pendentes = pendentes + urgentes;

---


## BUG-03

**Título:** [UX] Formulário não é limpo após adicionar uma tarefa

**Severidade:** Baixa
**Justificativa da severidade:** Não impede o uso do sistema, mas prejudica a experiência do usuário ao exigir limpeza manual dos campos.

**Prioridade:** P3
**Justificativa da prioridade:** Problema de usabilidade com baixo impacto funcional.

**Ambiente:**
- Navegador: Chrome 121.0
- Sistema Operacional: Windows 11
- Versão da aplicação: TarefaQS v1.0.0

**Passos para reprodução:**
1. Preencher o formulário de criação de tarefa
2. Clicar em "Adicionar tarefa"
3. Observar os campos do formulário

**Resultado esperado:**
O formulário deveria ser limpo automaticamente após a criação da tarefa.

**Resultado obtido:**
Os campos permanecem preenchidos após o envio.

**Evidência:**
js
// form.reset();

---
