# 🔎 Formulário — Parte B

> Preencha uma seção por finding. O mínimo esperado é **6 findings**.

**Dupla:** [Nome 1 + RA] + [Nome 2 + RA]
**Data da revisão:** [DD/MM/AAAA]

---

**Dupla:** Guilherme Siqueira + [SEU RA]
**Data da revisão:** 23/04/2026

---

### Finding #1

**📍 Linha(s):** 10–13
**🏷 Rótulo:** blocker
**📂 Dimensão:** Segurança
**⚠️ Severidade:** Crítica

**🐛 Problema:**
A função `buscarUsuarioPorNome` constrói a query SQL por concatenação de string, permitindo SQL Injection.

**💡 Sugestão de correção:**
Utilizar query parametrizada para evitar injeção.

javascript
const query = "SELECT * FROM usuarios WHERE nome = ?";
return db.executarQuery(query, [nome]);

### Finding #2

📍 Linha(s): 5
🏷 Rótulo: nit
📂 Dimensão: Padrões
⚠️ Severidade: Baixa

🐛 Problema:
A constante TIPOS_VALIDOS é declarada, mas não é utilizada para validar o tipo de usuário no cadastro.

💡 Sugestão de correção:
Validar o campo tipo antes de inserir no banco.

if (!TIPOS_VALIDOS.includes(dados.tipo)) {
  throw new Error('Tipo de usuário inválido');
}

### Finding #3

📍 Linha(s): 15–28, 30–36
🏷 Rótulo: major
📂 Dimensão: Erros
⚠️ Severidade: Média

🐛 Problema:
As funções assíncronas (cadastrarUsuario, atualizarEmail) não possuem tratamento de erro (try/catch).

💡 Sugestão de correção:

try {
  await db.insert('usuarios', usuario);
} catch (erro) {
  logger.error('Erro ao cadastrar usuário', erro);
  throw erro;
}
Finding #4

📍 Linha(s): 38–97
🏷 Rótulo: major
📂 Dimensão: Complexidade
⚠️ Severidade: Alta

🐛 Problema:
A função calcularLimiteEmprestimo possui alta complexidade ciclomática, com muitos if/else aninhados, dificultando manutenção.

💡 Sugestão de correção:
Refatorar utilizando funções auxiliares ou early returns.

if (usuario.tipo === 'professor') {
  return calcularLimiteProfessor(usuario);
}
Finding #5

📍 Linha(s): 38–97 e 99–136
🏷 Rótulo: major
📂 Dimensão: Padrões
⚠️ Severidade: Média

🐛 Problema:
Há duplicação de lógica entre calcularLimiteEmprestimo e calcularLimiteComSuspensao.

💡 Sugestão de correção:
Extrair lógica comum para funções reutilizáveis.

function calcularBaseProfessor(usuario) {
  // lógica comum
}
Finding #6

📍 Linha(s): 30–36
🏷 Rótulo: nit
📂 Dimensão: Legibilidade
⚠️ Severidade: Baixa

🐛 Problema:
Uso de variável com nome pouco descritivo (u), dificultando entendimento do código.

💡 Sugestão de correção:

const usuario = await db.buscarPorId('usuarios', id);
usuario.email = novoEmail;

---

✅ Checklist final

 Há pelo menos 6 findings preenchidas
 Cada finding cita linha, dimensão, rótulo e severidade
 As sugestões são concretas e acionáveis
 Pelo menos uma finding cobre segurança
 Pelo menos uma finding cobre complexidade


 ## Reflexão final

A atividade permitiu compreender, na prática, a importância de identificar defeitos tanto na execução quanto na análise estática do código. A elaboração dos bug reports reforçou a necessidade de clareza, reprodutibilidade e justificativa técnica, enquanto o code review evidenciou como problemas críticos — como falhas de segurança, ausência de tratamento de erros e alta complexidade — podem passar despercebidos sem uma análise estruturada.

Além disso, ficou evidente que boas práticas, como validação de dados, uso de padrões e escrita de código legível, são essenciais para garantir qualidade e manutenção do sistema. O exercício também mostrou como o trabalho em dupla e a revisão sistemática contribuem para uma visão mais completa do código, aproximando a atividade de um cenário real de desenvolvimento profissional.