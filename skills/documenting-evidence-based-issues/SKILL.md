---
name: documenting-evidence-based-issues
description: Use quando investigar ou relatar um defeito, especialmente com evidências incompletas ou quando o bug report precisar de diagnóstico, passos de reprodução, sugestão de correção ou critérios de aceite.
---

# Documentação de issues baseada em evidências

## Objetivo

Produza relatos de bugs úteis para engenharia sem transformar suposições em fatos. Separe o que foi observado, o que a inspeção do código confirma e o que continua sendo hipótese. Preserve as incertezas e evite exagerar conclusões sobre segurança, escopo ou cobertura de testes.

## Trabalhe em conjunto com Superpowers

Use esta skill junto com as skills pertinentes do Superpowers; ela não as substitui. Use `systematic-debugging` ao investigar um defeito técnico e `verification-before-completion` antes de afirmar que uma issue foi aberta, que uma evidência foi verificada ou que o relato está concluído. Use `brainstorming` se a tarefa se expandir para projetar comportamento novo ou uma solução mais ampla. Não invoque skills de implementação quando o pedido for apenas diagnosticar ou relatar.

## Fluxo de trabalho

1. **Registre o contexto do relato.** Anote ambiente/build, ator/perfil e tenant/escopo se conhecidos e pertinentes, operação executada e impacto observado. Nunca inclua credenciais, tokens, dados reais de pacientes ou outros segredos.
2. **Separe evidência de interpretação.** Identifique o que vem de relato do usuário, captura de tela, resposta da API, logs, testes automatizados ou inspeção local do código. Não sugira que uma captura prova persistência, autorização ou estado do backend se ela não demonstra isso.
3. **Reproduza com segurança quando autorizado e viável.** Respeite o escopo do usuário. Não faça gravações em produção, altere dados nem teste fora do ambiente solicitado. Se não houver reprodução, diga isso explicitamente.
4. **Investigue antes de afirmar causa-raiz.** Rastreie os caminhos relevantes da interface, API e persistência conforme necessário. Cite caminhos relativos do repositório e linhas quando disponíveis. Diferencie o comportamento confirmado no código local da versão implantada: o código local não prova qual versão está em STG/produção.
5. **Classifique o achado com precisão.** Diferencie falha de interface/mensagem, funcionalidade, integridade de dados e autorização/segurança. Um sintoma suspeito não comprova incidente de segurança. Declare o que as evidências demonstram e o que não demonstram.
6. **Escreva um relato acionável.** Inclua passos concisos de reprodução, comportamento esperado e observado, evidências, diagnóstico (ou declare que a causa não foi confirmada), direção sugerida sem implementar algo não solicitado e critérios de aceite testáveis.
7. **Declare os limites.** Informe cenários não testados, ausência de build/request/logs/banco e se código ou dados foram alterados. Nunca marque teste como aprovado com base em suposição.
8. **Verifique duplicatas e publique somente quando solicitado.** Pesquise issues abertas e fechadas no repositório relevante. Se a criação não foi solicitada, prepare um rascunho em vez de publicar. Não altere código do produto quando o pedido for somente relatar o bug.

## Linguagem para evidências

Use rótulos explícitos quando ajudarem:

- **Observado:** diretamente visível ou retornado na evidência fornecida/coletada.
- **Confirmado por inspeção do código:** comportamento presente no código local examinado; a versão implantada pode ser diferente.
- **Relatado pelo usuário:** informação fornecida, mas não verificada independentemente.
- **Hipótese / risco a investigar:** implicação plausível ainda não reproduzida ou comprovada.
- **Não testado / desconhecido:** evidência ou cenário necessário está ausente.

Prefira conclusões calibradas como “é compatível com”, “sugere” ou “não foi demonstrado” quando a evidência for incompleta. Use “causa confirmada”, “vazamento de dados” e “reproduzido” somente com evidências que sustentem essas afirmações.

## Estrutura sugerida para a issue

```markdown
## Problema
<Comportamento observado e impacto; sem causa especulativa.>

## Reprodução
1. <Passos mínimos, seguros e determinísticos>

## Evidência
<Origem da evidência, resposta/logs sanitizados e ambiente/build se conhecidos.>
<Declare o que a evidência não comprova.>

## Diagnóstico no código (se inspecionado)
- <caminho:linhas — comportamento local confirmado>
- <Incerteza sobre implantação e hipóteses ainda não confirmadas.>

## Esperado
- <Comportamento visível para o usuário e para o sistema>

## Sugestão de correção (opcional)
1. <Direção que preserve segurança/integridade; não prescreva uma correção para causa não confirmada.>

## Critérios de aceite
- [ ] <Resultados observáveis e testáveis, incluindo regressões/casos de borda pertinentes>

## Limites
<Não reproduzido, build/request/log/banco desconhecidos, cenários não testados e alterações de código/dados.>
```

Adapte ou omita seções que não se aplicam. Mantenha a issue proporcional ao defeito; não acrescente critérios genéricos apenas para preencher espaço.

## Verificações de segurança e rigor

Antes de publicar, confira:

- Toda afirmação factual informa sua fonte?
- Relatos do usuário, evidência direta, inspeção do código e hipóteses estão claramente separados?
- Um 404, lista vazia ou erro genérico pode ter mais de uma explicação? Não reduza as alternativas sem evidência.
- O relato evita afirmar falha de autorização ou exposição de dados sem demonstrar acesso não autorizado?
- Os critérios de aceite são testáveis e cobrem o limite de segurança sem sugerir atalhos inseguros?
- Exemplos sensíveis usam dados sintéticos e sanitizados?
- A issue está dentro do pedido, sem implementar uma correção não solicitada?

Se a causa-raiz for desconhecida, intitule e descreva a issue pelo sintoma observado e identifique o diagnóstico como não confirmado.
