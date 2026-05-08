# dev-template

Template de devcontainer para projetos derivados do [devbase](https://github.com/evanbs/devbase).

## Onboarding — configure uma vez, use em todos os projetos

### 1. Crie seus dotfiles pessoais

Fork ou copie o repositório [dev-dotfiles](https://github.com/evanbs/dev-dotfiles),
edite `git/.gitconfig` com seu nome e e-mail, e publique na sua conta GitHub.

### 2. Configure o VSCode

`Ctrl+,` → buscar "dotfiles":

```json
{
  "dotfiles.repository": "<seu-usuario>/<seu-repo-dotfiles>",
  "dotfiles.targetPath": "~/dotfiles",
  "dotfiles.installCommand": "install.sh"
}
```

Feito isso, qualquer container que você abrir terá automaticamente
seu gitconfig, starship e aliases — sem mais nenhuma configuração.

### 3. Use o template em um projeto novo

Copie a pasta da stack desejada para `.devcontainer/` no novo repo:

```bash
cp -r .devcontainer/<stack>/ ~/projetos/meu-projeto/.devcontainer/
```

Ao abrir no VSCode → selecione o container → o `devbase-setup` substituirá
`{{PROJECT_NAME}}` pelo nome do projeto automaticamente.

---

## Stacks disponíveis

| Stack | O que adiciona | Mecanismo |
|---|---|---|
| `base` | Só a imagem base | — |
| `node` | Node LTS + fnm (já na imagem) | — |
| `bun` | Bun runtime | instalador oficial via postCreateCommand |
| `python` | Python 3.12 + pyenv | devcontainer feature oficial MS |
| `dotnet` | .NET SDK latest | devcontainer feature oficial MS |
| `java` | Java 21 + SDKMAN | devcontainer feature oficial MS |

> Android será adicionado posteriormente.

## O que vem em todas as stacks (imagem base)

- Shell: zsh + oh-my-zsh + starship
- Git: git, git-delta
- Node LTS + fnm (gerenciamento de versões via `.node-version`)
- Ferramentas: eza, bat, ripgrep, fzf, jq, httpyac, p7zip
