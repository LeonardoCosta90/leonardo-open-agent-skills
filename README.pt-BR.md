# Skills abertas para agentes — Leonardo

[Read in English](README.md)

Skills reutilizáveis para agentes de IA, mantidas em arquivos portáveis `SKILL.md`. Elas podem ser usadas em diferentes projetos. Quando uma skill for pertinente, use-a em conjunto com as skills aplicáveis do **Superpowers**; uma não substitui a outra.

## Skills disponíveis

| Skill | Para que serve |
|---|---|
| [`conducting-functional-qa`](skills/conducting-functional-qa/SKILL.md) | Conduzir testes funcionais manuais passo a passo e registrar apenas resultados sustentados por evidências. |
| [`documenting-evidence-based-issues`](skills/documenting-evidence-based-issues/SKILL.md) | Criar relatos de bugs acionáveis, separando evidências, análise do código, hipóteses e limitações. |

## Instalação no OpenCode

O OpenCode encontra skills pessoais em `~/.agents/skills/`. Clone este repositório e copie as pastas das skills para esse local:

```sh
git clone https://github.com/LeonardoCosta90/leonardo-open-agent-skills.git
cp -R leonardo-open-agent-skills/skills/* ~/.agents/skills/
```

Também é possível copiar uma única pasta de skill para `.opencode/skills/` dentro de um projeto. Cada skill deve permanecer em sua própria pasta e conter um arquivo `SKILL.md`.

Se uma skill recém-instalada ainda não aparecer, recarregue o OpenCode ou inicie uma nova sessão.

## Estrutura do repositório

```text
skills/
  <nome-da-skill>/
    SKILL.md
```

## Contribuição

Consulte [CONTRIBUTING.pt-BR.md](CONTRIBUTING.pt-BR.md) para orientações sobre formato, qualidade e pull requests. Mantenha as skills focadas, reutilizáveis e claras sobre quando devem ser usadas. Não inclua segredos, dados pessoais ou informações privadas específicas de projetos.
