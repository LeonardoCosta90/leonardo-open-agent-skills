# Como contribuir

[Read in English](CONTRIBUTING.md)

## Como adicionar ou atualizar uma skill

1. Crie `skills/<nome-da-skill>/SKILL.md`, usando um nome de pasta em minúsculas e separado por hífens.
2. Inclua metadados YAML com `name` e `description`. A descrição deve começar com **“Use when...”** e explicar em quais situações a skill deve ser carregada.
3. Escreva instruções reutilizáveis entre projetos. Procedimentos específicos de um projeto devem ficar na documentação desse projeto.
4. Explique como a skill se integra às skills relevantes do Superpowers. Use apenas as que se aplicam; não torne obrigatórios fluxos sem relação com a tarefa.
5. Inclua verificações concretas de evidência, segurança e conclusão quando forem pertinentes.
6. Atualize a lista de skills e as instruções de instalação no README quando necessário.
7. Revise a skill com cenários realistas antes de considerá-la pronta, incluindo casos com evidências ausentes e pressão para afirmar além do que foi comprovado.

## Pull requests

Descreva o caso de uso, as situações que devem ativar a skill e os cenários usados para validá-la. Não inclua credenciais, tokens, dados de clientes ou capturas/logs sem sanitização.

## Estilo

- Prefira instruções concisas, diretas e com critérios observáveis.
- Separe fatos, relatos de usuários, hipóteses e informações desconhecidas.
- Não declare testes aprovados ou defeitos confirmados sem evidências.
- Mantenha as skills independentes; referencie outras pelo nome reconhecível.
