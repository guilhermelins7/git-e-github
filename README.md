<div align="center"><img src="images/git-e-github.png" width="100%"></div>

# GIT Fundamental:

## Comandos Básicos para terminal Bash:

```bash
cd <camninho> # cd(Change Directory)
ls || ls -al # lista diretório atual || lista arquivos ocultos.
clear # Limpa o terminal.
cat # exibir conteudo do arquivo por código no terminal
pwd # exibir caminho da pasta atual. (print working diretory)
mkdir # criar nova pasta no diretório (make directory)
```

## Git - Sistema de versionamento:

você controla as modificações de um projeto por meio de versões chamadas "commits".

## GitHub - serviço online de hospedagem de repositórios Git remotos.

- Possui uma interface gráfica web: [github.com](http://github.com/)
- É uma plataforma social (usuários, página de perfil, seguidores, colaboração, etc.). Dica: currículo!
- Maior serviço do mundo de hospedagem de projetos de código aberto
- Modelo de cobrança: gratuito para projetos de código aberto, pago para projetos privados
- Alternativas: BitBucket, GitLab, etc.

# Repositório remoto e local:

- Um projeto controlado pelo Git é chamado de **repositório** de versionamento.
- Tipicamente uma cópia "oficial" do repositório fica salvo em um **servidor** (**repositório remoto**).
- Cada desenvolvedor que trabalha no projeto pode fazer uma cópia do repositório para seu computador (**repositório local**). Alterações podem ser feitas localmente no projeto (novos commits) e depois enviadas para o servidor remoto.

# Configurando identificação no Git:

```bash
git config --global user.name "Seu nome" # Configurar nome.

git config --global user.email "Seu email de cadastro do Github" # e-mail.

git config --global int.defaultBranch <main> # Configurar branch principal

git config --global core.editor <editor> # Configurar Editor Principal

git config --list # visualizar alterações.
```

### Removendo configuração errada:

```bash
git config --global --unset <tag ex: user.nome>
```

### Checar localização da configuração em arquivo:

```bash
git config --global --show-origin <condiguracao_global>
																	# exemplo: user.name || user.email
```

# Comandos básicos de git:

```bash
# Importante sempre checar o repositório atual com status para checar repo existente.
git status # Checar alterações e estado atual do repositório.

git init # Criar repostiório local

git add <file> | . # selecionar arquivos para passar para "área de stage"

git commit -m 'mensagem' # Salvar alterações/"fazer commit".
# podendo ser tanto aspas simples '' ou duplas "".
```

# Utilizando GitHub:

## Configurar chave SSH para o Github:

- O Github aboliu a autenticação somente com usuário e senha.

### **Secure Shell Protocol (SSH)**:

A ideia básica é cadastrar previamente quais computadores podem acessar o Github em seu nome. Outros computadores não conseguem acessar

### Verificar se há chaves SSH:

```bash
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

### Gerar nova chave SSH:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Copiar chave SSH gerada:

```bash
$ clip < ~/.ssh/id_ed25519.pub
# Copies the contents of the id_ed25519.pub file to your clipboard
```

## Utilizando token:

A chave token é obtida no GitHub, na área de “Developer Settings”.

### Configurando token localmente:

```bash
git config --global credential.helper store # para gravar permanentemente.
git config --global credential.helper cache # para gravar temporariamente.
```

# Lidando com repositórios remotos:

```bash
git clone <projeto_git> # utilizado para clonar repositórios já existentes

git remote add <nome-remoto> <url || sshKey> # adicionar repositório remoto ao local.
# Atenção!: <nome-remoto> normalmente é "origin".

git remote -v # Listar repositórios remotos associados ao projeto.

git remote remove <origin> # Desvincular repositório remoto.

git push # subir alterações para o GitHub.

git pull # baixar alterações do repositório remoto (Utilizar sempre antes do merge)
```

## Adicionando Colaboradores no repositório remoto:

- Poder ser feito através das configurações do projeto e incluindo o user name do colaborador. Uma solicitação para participação será enviada para o GitHub e e-mail do colaborador.

## Definir coautores no commit:

O Git oferece a possibilidade de adicionar **mais de um autor** a um commit. Para isso, após escrever a mensagem do commit, pulamos duas linhas e usamos a palavra-chave `Co-authored-by:`, seguido do nome e e-mail associado ao GitHub (entre < >) de cada pessoa colaboradora.

```bash
$ git commit -m "Adicionar nova funcionalidade.
>
>
Co-authored-by: NOME <nome@email.com>
Co-authored-by: OUTRO-NOME <outro@email.com>"
```

# Melhorando Descrições de Commits

Mensagens de commits devem ser **claras e objetivas** para facilitar a compreensão do histórico de alterações no projeto. A seguir, algumas diretrizes para escrever commits eficazes:

## Boas práticas para escrever commits

- **Seja conciso e direto:** A primeira linha da mensagem deve conter, no máximo, **72 caracteres**. Se precisar adicionar mais detalhes, utilize uma nova mensagem com `m` ou um corpo de descrição separado.
- **Use verbos no infinitivo:** Comece a mensagem com um verbo no infinitivo que descreva a ação realizada, como "adicionar", "corrigir" ou "atualizar". _Exemplo:_
  - ✅ `"Atualizar texto do título da página"`
  - ❌ `"Atualizado o título da página"`
- **Evite detalhes técnicos excessivos:** Mensagens de commit devem descrever a mudança de forma compreensível para toda a equipe. Informações mais técnicas podem ser detalhadas nos comentários do código ou na documentação.

🔹 _Lembre-se: o histórico de commits serve como documentação do projeto. Quem for ler suas mensagens pode não ter o contexto original, então escreva de forma clara e descritiva._

## Conventional Commits

O padrão [**Conventional Commits**](https://www.conventionalcommits.org/pt-br/v1.0.0/) ajuda a manter consistência e organização no histórico de commits.

### Principais tipos de commits

| Tipo         | Descrição                                         | Exemplo                                                   |
| ------------ | ------------------------------------------------- | --------------------------------------------------------- |
| **feat**     | Adição de uma nova funcionalidade.                | `feat: implementar método para criação de conta bancária` |
| **fix**      | Correção de bugs.                                 | `fix: corrigir cálculo de saldo ao transferir fundos`     |
| **refactor** | Melhorias no código sem alterar a funcionalidade. | `refactor: simplificar lógica do método Depositar`        |
| **docs**     | Alteração na documentação.                        | `docs: adicionar explicação para o método Sacar`          |

Seguir essas diretrizes ajuda a manter um histórico limpo e compreensível para todos os colaboradores do projeto. 🚀

# Software Livre e Open Source, um pouco sobre a história e diferenças:

[Open source: o que é e como funciona o código aberto? | Alura](https://www.alura.com.br/artigos/open-source-uma-breve-introducao)

### Fork:

O **fork** no GitHub cria uma cópia independente de um repositório, permitindo modificações sem impactar o projeto original. Ele é amplamente utilizado para contribuir com projetos open source ou personalizar um repositório existente.

### Quando usar um fork?

✔ Para contribuir com projetos sem permissão de escrita no repositório original.

✔ Para experimentar mudanças sem afetar o código principal.

✔ Para criar uma base de desenvolvimento própria a partir de outro projeto.

# Trabalhando com Branches (ramificações):

## Entendendo mais sobre branches:

Usadas para criar linhas de desenvolvimento paralelas e independentes. Funcionalidade fundamental para trabalhar com novas funcionalidades (features)

### Comandos principais:

```bash
# Criar novas branchs:
git branch <nome_branch> # Apenas cria a branch, mantendo na atual.
git checkout -b <branch> # Cria nova branch e já troca para a criada.

# Visualizar branchs existentes.
git branch

# Renomear branch existente
git branch -m <nomeAtual> <NovoNome>

# Trocar de branch:
git checkout <branch>
# ou
git switch <branch>

#Remover uma branch:
git branch -d <branch>
```

### Subir nova branch para aprovação no repositório remoto:

- Após criar uma nova branch localmente e tentar envia-la ao GitHub (sem mesclar), se faz necessário também usar o push definindo o Upstream (rastreamento) no repositório remoto, para isso, o comando usado é similar ao push de criação de projeto:

```bash
git push --set-upstream origin <branch>
# ou sua forma abreviada:
git push -u origin <branch> # na primeira vez após ser criada.
```

### Excluir Branch em repositório remoto após atualizações:

```bash
git branch -D <nomeBranch> # excluir branch que possui modificações.
git push origin :nomeBranchExcluida # para excluir também do repositório remoto.
```

## Rebase vs Merge: Como mesclar branchs e boas práticas:

### git branch:

- Normalmente é executado estando na branch principal (main), referenciando a branch a qual deseja mesclar com a main.

```bash
git merge <nome_branch> # vai pegar os commits da branhc e uni-los à branch atual.
```

### git rebase:

sua principal diferença é que ele aplica a prática de **fat forward**, por isso ao realizar o `rebase`, todos os commits da outra *branch* são adicionados **antes** do primeiro commit da nossa *branch* atual, reescrevendo a história. Isso faz com que novas alterações possam ser integradas à nossa branch e permite que quando formos realizar o `merge`, não seja necessário um *merge commit*, garantindo o *fast forward*.

```bash
git rebase <nomeBranch> # Esse comando normalmente é utilizado a parte da main/produção.
```

### Merge & Fast-forward:

O **merge** é a operação que une diferentes branches no Git. Ele pode acontecer de duas formas principais:

1. **Fast-forward**: Ocorre quando a branch de destino não tem commits novos em relação à branch que está sendo mesclada. O Git simplesmente avança o ponteiro da branch de destino para o commit mais recente da outra branch, sem criar um novo commit de merge.
2. **Merge com commit**: Se houver divergências entre as branches (ou seja, novos commits em ambas), o Git cria um novo commit de merge para unir as alterações, mantendo o histórico dos dois lados.

# Fluxo de Trabalho com Git e GitHub

Este fluxo organiza o desenvolvimento, garantindo código de qualidade e colaboração eficiente.

## 1. Criar uma Branch

Antes de iniciar uma nova funcionalidade ou correção, crie uma branch baseada na `main` ou `develop`:

```bash
git checkout -b feat/nova-feature
```

## 2. Enviar para o Repositório

Envie sua branch com alterações para o repositório remoto no GitHub:

```bash
git push origin feat/nova-feature
```

## 3. Criar um Pull Request (PR)

- Acesse o GitHub e clique em **"Compare & pull request"**.
- Defina a branch de destino (`main` ou `develop`).
- Descreva as mudanças e solicite revisão.

## 4. Revisão de Código

- O time revisa o PR e pode aprovar ou solicitar mudanças.
- Se necessário, ajuste o código, faça novos commits e envie novamente com `git push`.

## 5. Fazer o Merge

Após aprovação, escolha uma opção de merge no GitHub:

- **Merge commit**: Mantém histórico completo.
- **Squash and merge**: Consolida os commits em um só.
- **Rebase and merge**: Aplica os commits no topo da branch de destino.

## 6. Atualizar o Ambiente Local

Mantenha seu repositório atualizado antes de novas tarefas:

```bash
git checkout main
git pull origin main
git switch -c nova-branch
```

# Trabalhando com Arquivos:

### Remover arquivo do repositório:

```bash
git rm <nome do arquivo> # remover arquivos
```

### Recuperando arquivos excluídos:

- Após utilizar o comando acima, a informação do arquivo deletado estará na área de stage, para reverter a exclusão, se faz necessário primeiramente retirar a mudança do stage:

```bash
git reset # retirar arquivos do stage
```

- Após isso, o arquivo pode ser recuperado com o comando abaixo:

```bash
git restore <nome_do_arquivo>
```

### Movendo arquivos e renomeando:

- O comando abaixo pode ser utilizado tanto para mover quanto para renomear arquivos (podendo ser feito até os dois ao mesmo tempo).

```bash
git mv <nome_do_arquivo> <endereco_destino/nome_do_arquivo[pode ser renomeado]>
```

### Revertendo modificações em Arquivos:

```bash
git checkout <nome_do_arquivo> # retorna ao estado dele no commit atual
```

## Ignorando arquivos não desejados (gitignore):

Através do arquivo .gitignore é possível definir quais arquivos não devem ser passados para o gitinore. Existem sites na web que geram esses arquivos de acordo com a tecnologia usada, como exemplo abaixo:

[gitignore.io](https://www.toptal.com/developers/gitignore/)

Geralmente o arquivo .gitignore fica salvo na pasta principal do repositório. Mas também é possível salvar outros arquivos .gitignore em subpastas do repositório, para indicar o que deve ser ignorado por cada subpasta. Como em projetos de back e front end em diferentes frameworks e com diferentes tipos de arquivos que devem ser iginorados.

### Casos comuns de arquivos que não devem ser salvos pelo Git:

- **Arquivos Compilados:**

Linguagens compiladas (C, C++, Java, C#, etc.) geram arquivos de código compilado para executar o programa localmente.

- **Arquivos de bibliotecas externas usadas no projeto:**

Projetos reais utilizam bibliotecas externas (programas prontos disponíveis na Internet). Por exemplo, projetos JavaScript com NPM tipicamente salvam uma subpasta "node_modules" na pasta do seu projeto.

- **Arquivos de configuração da sua IDE:**

IDE's podem salvar uma subpasta com arquivos de configuração na pasta do projeto (exemplo: .vscode).

- **Arquivos de configuração do seu sistema**

Por exemplo, sistemas Mac podem gravar uma subpasta .ds_store na pasta do projeto.

# Exibindo histórico de versionamento:

### git log:

Ao utilizar git log você consegue visualizar uma lista dos últimos commits feitos ou até mesmo commits para arquivos em específico.

```bash
git log # Exibe últimos commits feitos, do mais recente para mais antigo.
git log <arquivo> # Exibe commits feitos que envolvem o arquivo definito.
git log --oneline # Exibe commits de forma simplificada, organizados em uma única linha.
git log -p # Visualizar histórico + alterações realizadas em cada commit.
git log --graph # Visualização em grafo de acordo com branchs.

# opções de personalização:

git log --pretty
git log --format

# exibindo o log e outra branch:
git log <branch>
```

## Exibir histórico geral do projeto:

### git reflog:

esse comando é muito útil quando usado junto ao cherry-pick, pois através dele é possível visualizar todo o histórico do projeto em formato de pilha, mesmo os de branches já excluidas.

```bash
git reflog
```

## Verificando Alterações (git show & diff):

### git diff (diferença entre dois pontos)

```bash
git diff
# Exibe diferença de arquivos que estão fora do stage, exibindo o que foi ...
# ... adicionado ou removido.

git diff <aquivo> # Exibe diferenças de um determinado arquivo.
git diff <hash1> <hash2> # Exibe diferenças entre dois commits realizados.
```

### git show (diferenças entre versões):

```bash
git show # Exibe as mudanças realizadas nos arquivos de acordo com último commit.
git show <hash> # Exibe as mudanças de um commit em específico.
```

# Alterando Histórico e descartando alterações:

## Remover commits do histórico:

```bash
git reset --hard <hash> # voltar ao estado do hash indicado e excluir commits seguintes.

# importante sempre fazer essa alteração quando não estiver sincronizado com remoto.
```

## Descartando alterações com git restore:

```bash
git restore . || <arquivo> # descarta as alterações atuais.
git restore --staged <arquivo> # retirar arquivos da área de stage.
git restore source=HASH <arquivo> # Retornar arquivo para estado de um commit.
```

## Revertendo Commits:

### Git Revert:

Ao utilizar git revert, podemos reverter um commit que foi realizado para o seu estado original, basicamente será feito um novo commit com a reversão.

```bash
git revert HEAD # Reverte o commit mais recente.
git revert <hash> # Reverte o commit indicado, voltando ao estado anterior.

# esse comando mantém o histórico de commits
```

### Em caso de conflitos:

```bash
git revert --abort # Aborta uma versão que está em tratamento.
git revert --continue # Após alterações e correções, finaliza o revert.
```

# Git Checkout:

### Commit:

Utilizar o git checkout, você consegue visualizar como estavam como estavam seus arquivos para um determinado commit.

```bash
git checkout <commit>
# volta o seu ambiente de trabalho para o estado de como estavam os arquivos
# - nesse commit em específico.
```

```bash
gic checkout <branch>
# Volta o seu ambiente para o estado mais atual da branch definida.
```

# Guardando alterações temporariamente:

## git stash:

`git stash` arquiva (ou *faz o stash*) de alterações atuais para que seja possível trabalhar em outra coisa, depois voltar e fazer a reaplicação mais tarde. O stashing é útil quando você precisa alternar com rapidez a branch e trabalhar em outra coisa, mas está no meio da alteração de código e não está pronto para fazer commit.

```bash
git stash # cria um stashing com as alterações atuais a branch.

git stash pus -m "nome_previo_alteracoes" # crie um stashing com descrição.

git stash list # exibe a lista de stashs, organizados em pilha.
git stash list clear # limpa toda a lista de stash.

git stash pop # aplica as alterações do último stash realizado.
git stash po <indice> # aplica as alterações e retira da lista.

git stash apply {indexStash} # aplica as alterações com base no indice.
# importante se atentar que esse comando não remove o stash da lista.

git stash drop # Remove o último stash da pilha sem aplicar as alterações (excluir)
git stash drop <indice> # Remove o stash com base no indice. (excluir)
```

# Criando versões do projeto: (git tag):

```bash
git tag <tagName> # Definir uma tag no commit atual.
git tag <tagName> <hash> # Definir uma tag para um commit específico.

# Subindo tags (git push não envia por padrão.):
git push origin <tagName> # Subir alterações até uma Tag específica.
git push --tags # subir todasa tags.

# Exlcuir tags:
git tag -d <tagName>

# Tags com descrições (Annotated tags):
git tag -a <tagName> -m "mensagens" # notar que o -a é opcional.
# Tags com descrições possuem detalhes que podem ser vistos com:
git tag -v <tagName>
```

# Cherry-pick: aplicando commits de outra branch:

- através do cherry-pick, é possível aplicar um commit específico utilizando seu hash e aplica-lo na branch atual.

```bash
git cherry-pick <hash> # Deve ser utilizado na branch que pretende aplicar.
```

# Encontrando autores de alterações:

## git blame:

- Esse comando exibe os autores e o hash do commit das últimas alterações em determinado arquivo, assim possibilitando tirar dúvidas sobre funcionalidades.

```bash
git blame <nomeArquivo> # deve sempre ser indicado um arquivo para checar.
```
