# dev-template

Template de devcontainer para projetos derivados do [devbase](https://github.com/evanbs/devbase).

## Como usar

Copie a pasta da stack do seu projeto para `.devcontainer/` no novo repo:

```bash
cp -r .devcontainer/<stack>/ ~/projetos/meu-projeto/.devcontainer/
```

Ao abrir no VSCode, o `devbase-setup` substituirá `{{PROJECT_NAME}}` pelo nome do projeto.

## Stacks disponíveis

| Stack | O que adiciona | Feature |
|---|---|---|
| `base` | Só a imagem base | — |
| `node` | Node LTS + fnm (já na imagem) | — |
| `bun` | Bun runtime via instalador oficial | postCreateCommand |
| `python` | Python 3.12 + pyenv | devcontainer feature oficial |
| `dotnet` | .NET SDK (versão latest) | devcontainer feature oficial |
| `java` | Java 21 + SDKMAN | devcontainer feature oficial |

> Android será adicionado posteriormente.

## O que vem na imagem base

Todas as stacks herdam o [devbase](https://github.com/evanbs/devbase):

- Shell: zsh + oh-my-zsh + starship
- Git: git, git-delta, gh
- Node LTS + fnm (gerenciamento de versões)
- Ferramentas: eza, bat, ripgrep, fzf, jq, httpyac, p7zip

## Dotfiles

Configs pessoais (starship, gitconfig, aliases) são injetadas automaticamente
pelo VSCode via `dotfiles.repository` — configure uma vez em Settings:

```json
{
  "dotfiles.repository": "evanbs/dev-dotfiles",
  "dotfiles.targetPath": "~/dotfiles",
  "dotfiles.installCommand": "install.sh"
}
```
