---
name: conducting-functional-qa
description: Use quando estiver orientando QA funcional manual em uma aplicação ativa, continuando um plano de testes, coletando evidências da interface ou registrando resultados em um tracker ou wiki de QA.
---

# Condução de QA funcional

## Princípio central

A pessoa operadora executa o teste no sistema ativo. Oriente uma ação significativa por vez e registre apenas resultados que ela relatou explicitamente ou que a evidência demonstra diretamente. Um plano de testes não autoriza acessar sistemas, criar dados ou fazer alterações.

## Trabalhe em conjunto com Superpowers

Use esta skill junto com as skills pertinentes do Superpowers; este fluxo não as substitui. Use `systematic-debugging` antes de diagnosticar um resultado inesperado ou falha de teste, e `verification-before-completion` antes de afirmar que um teste, atualização de registro ou publicação foi concluído. Use `brainstorming` antes de inventar ou alterar materialmente o escopo dos testes. Não invoque skills de implementação ou planejamento quando a tarefa for apenas orientar a execução manual e registrar resultados.

## Fluxo de trabalho

1. **Leia a fonte de testes e o histórico.** Encontre o próximo caso aplicável ainda não concluído. Confira a wiki/tracker e as notas recentes; não repita testes já concluídos, salvo se o usuário pedir reteste ou novas evidências justificarem.
2. **Respeite o escopo e as exclusões.** Preserve as restrições explícitas: ambientes bloqueados, módulos excluídos, problemas conhecidos que não devem ser reabertos, casos pulados, perfis de usuário, privacidade e limites para acesso direto à API/banco. Peça autorização antes de ampliar o escopo.
3. **Escolha o próximo teste seguro e útil.** Prefira o próximo caso funcional que possa ser exercitado pela interface disponível. Evite casos cuja pré-condição esteja bloqueada. Identifique dados sintéticos e requisitos de limpeza antes de ações com consequências.
4. **Oriente de forma incremental.** Apresente ID e nome do caso, passos claros e resultado esperado observável. Aguarde evidências da pessoa operadora antes de decidir ou avançar para a próxima ação relevante. Não peça que ela infira persistência no backend a partir de um estado transitório da interface.
5. **Avalie a evidência sem extrapolar.** Separe relato da pessoa operadora, capturas, interface visível, resposta da API, estado persistido e inspeção de código. Aponte o que ainda não foi verificado. Um clique bem-sucedido não comprova persistência, limites de autorização nem funcionamento ponta a ponta.
6. **Classifique corretamente.** Use status do tracker, como OK, Não OK, Bloqueado ou N/A, somente quando houver suporte. Um teste é **OK** apenas para o escopo declarado e os critérios de aceite observados. Use **Não OK** para divergência demonstrada. Use **Bloqueado** quando uma pré-condição ou ambiente impedir a execução. Use **N/A** somente com justificativa explícita. Teste pulado ou adiado continua sem marcação, a menos que exista status próprio e o usuário aprove seu uso.
7. **Trate falhas e issues.** Diante de resultado inesperado, preserve evidências sanitizadas e investigue antes de afirmar a causa. Crie ou atualize issue somente quando solicitado ou autorizado pela tarefa em andamento; pesquise duplicatas antes. Não altere código do produto quando a tarefa for apenas executar ou registrar testes.
8. **Atualize os registros com cuidado.** Antes de editar wiki/tracker, confirme o caso e o conteúdo atual. Inclua evidência concisa, ambiente/build/perfil quando conhecidos, link do defeito e limitações. Não exponha credenciais nem dados pessoais. Não faça commit ou publicação externa, salvo se isso fizer parte da autorização já dada pelo usuário.
9. **Verifique a atualização.** Confira diff/formatação, confirme que somente os registros previstos foram alterados e valide a publicação se ela foi solicitada. Informe status, base de evidência, limitações e próximo caso elegível.

## Padrão de interação por etapa

Em cada turno, informe:

1. **Caso atual:** ID e título curto.
2. **Ação:** o que a pessoa deve fazer agora, usando dados sintéticos/não sensíveis.
3. **Observação esperada:** o que relatar ou capturar.
4. **Limite:** cautela, pré-condição ou área excluída pertinente.

Após receber evidências, resuma o que elas demonstram e o que não demonstram. Peça somente a próxima observação necessária; não marque resultados antecipadamente nem envie uma longa sequência de casos não relacionados.

## Tabela de decisão de status

| Status | Use quando | Não use quando |
|---|---|---|
| OK | Todos os critérios de aceite do escopo executado estão sustentados por evidências | Apenas parte foi executada, ou persistência/segurança foi inferida sem verificação |
| Não OK | Um resultado reproduzível ou diretamente observado viola o esperado | Há apenas uma mensagem suspeita, sem divergência demonstrada |
| Bloqueado | Uma pré-condição identificada (acesso, ambiente, dados, permissão) impede execução válida | O teste é apenas inconveniente ou foi intencionalmente pulado |
| N/A | O caso não se aplica, com justificativa aprovada/documentada | O caso simplesmente não foi executado |

Evidência parcial deve ser registrada como parcial, não promovida a aprovação completa. Se a fonte dos testes não tiver status parcial, mantenha a marcação oficial inalterada e adicione uma nota claramente identificada somente se autorizado.

## Segurança e rigor

- Nunca peça senhas, tokens, prontuários reais ou capturas sensíveis sem ocultação.
- Não contorne controles de acesso, investigue outros tenants nem faça alterações destrutivas/irreversíveis sem autorização explícita e plano de limpeza/reversão.
- Não repita casos já confirmados como concluídos; diferencie reteste de continuação ou cenário adicional.
- Não reabra problemas conhecidos nem áreas excluídas sem orientação do usuário.
- Não declare falha de segurança com base apenas em erro, lista vazia, diferença entre perfis ou elemento visível na interface.
- Não declare conclusão, aprovação, publicação ou persistência sem verificar a evidência correspondente.
