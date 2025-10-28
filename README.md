# 🧩 Aula Prática – Git Local (sem GitHub)

## 🎯 Objetivo
Aprender a utilizar o **Git** localmente para versionar projetos, criando commits, branches e manipulando o histórico de forma segura.

---

## 🧱 1. Configuração inicial

Esses comandos configuram o nome e o e-mail do usuário (necessário para registrar os commits).

```bash
git config --global user.name "Maria Clara"
git config --global user.email "mclarasgalindo@hotmail.com"
git config --global core.editor "code --wait"   # Define o VS Code como editor padrão (opcional)
git config --list                                # Verifica as configurações atuais
```
- O comando **git config --global user.name "Maria Clara"** define o nome que será exibido como autor das alterações (commits). Já o **git config --global user.email "mclarasgalindo@hotmail.com"** registra o e-mail que será associado ao seu nome, o que é importante para identificar você nos repositórios, especialmente no GitHub. O comando **git config --global core.editor "code --wait"** define o Visual Studio Code como o editor de texto padrão do Git, fazendo com que ele abra automaticamente quando for necessário editar mensagens de commit ou resolver conflitos. Por fim, **git config --list** mostra todas as configurações salvas, permitindo verificar se os dados foram definidos corretamente.

---

## 📂 2. Criar e iniciar um repositório

```bash
mkdir meu_projeto
cd meu_projeto
git init
```
- O comando **mkdir meu_projeto cria** uma nova pasta chamada meu_projeto. Em seguida, **cd meu_projeto** faz com que você entre nessa pasta (ou diretório) recém-criada. Por fim, **git init** transforma essa pasta em um repositório Git, ou seja, um local onde o Git vai começar a registrar as alterações feitas nos arquivos.Depois de rodar esses comandos, o Git cria uma subpasta oculta chamada **.git**, que guarda todas as informações de controle de versão. A partir daí, você pode adicionar arquivos, fazer commits e controlar o histórico do seu projeto.

> O comando `git init` cria um repositório local, gerando a pasta oculta `.git`.

---

## 🏷️ 3. Alterar a branch padrão de `master` para `main`

Por padrão, o Git pode criar a branch inicial como **master**.  
Para padronizar e seguir boas práticas, altere para **main**:

```bash
git branch -m master main
```

Se quiser definir **main** como padrão para novos repositórios:

```bash
git config --global init.defaultBranch main
```
- O comando **git branch -m master main** renomeia o ramo principal do repositório atual, trocando master por main. Já o comando **git config --global init.defaultBranch main** define que, em todos os novos repositórios criados no seu computador, o ramo principal se chamará main automaticamente. Isso ajuda a manter um padrão mais moderno e inclusivo nos projetos.

---

## 📄 4. Criar arquivos e verificar status

```bash
echo "Meu primeiro arquivo" > readme.txt
git status
```
- O comando **echo "Meu primeiro arquivo" > readme.txt** cria um arquivo chamado readme.txt e escreve dentro dele a frase “Meu primeiro arquivo”. Já o comando **git status** mostra a situação atual do repositório, indicando se há arquivos novos, modificados ou prontos para serem adicionados e confirmados (committed). Assim, você pode ver que o readme.txt foi criado, mas ainda não está sendo rastreado pelo Git.

> `git status` mostra arquivos novos, modificados ou prontos para commit.

---

## 🧺 5. Adicionar arquivos à área de staging

```bash
git add readme.txt       # adiciona um arquivo específico
git add .                # adiciona todos os arquivos do diretório
git status
```
- O comando **git add readme.txt** adiciona apenas o arquivo readme.txt à área de preparação (staging area), indicando que ele será incluído no próximo commit. Já o **git add .** adiciona todos os arquivos novos ou modificados do diretório atual de uma só vez. Em seguida, **git status** mostra o estado do repositório, permitindo ver quais arquivos foram adicionados e estão prontos para serem confirmados.

> A área de staging é onde os arquivos ficam “preparados” antes do commit.

---

## 💾 6. Fazer o primeiro commit

```bash
git commit -m "Primeiro commit - adiciona readme.txt"
```

- O **git commit -m "Primeiro commit - adiciona readme.txt"** cria um commit, ou seja, uma gravação no histórico do Git que guarda o estado atual dos arquivos adicionados. A opção **-m** permite escrever uma mensagem explicando o que foi feito nesse caso, informando que o arquivo readme.txt foi adicionado. Essa mensagem ajuda a entender as mudanças quando se analisa o histórico do projeto no futuro.

> Um commit é o “salvamento” oficial no histórico do repositório.

---

## 🔍 7. Ver histórico e detalhes

```bash
git log
git log --oneline
git show
```
- O comando **git log** mostra a lista completa de commits do repositório, incluindo o autor, data e a mensagem de cada um. Já o **git log --oneline** exibe o mesmo histórico, mas de forma resumida, mostrando apenas o código curto do commit e sua mensagem útil para ter uma visão rápida. Por fim, **git show** exibe os detalhes de um commit específico, como as linhas de código que foram adicionadas, modificadas ou removidas, ajudando a entender exatamente o que mudou em cada atualização.

> Use `--oneline` para visualizar um resumo simplificado.

---

## ✏️ 8. Editar arquivos e registrar mudanças

```bash
echo "Adicionando nova linha" >> readme.txt
git status
git diff
git add readme.txt
git commit -m "Atualiza readme.txt com nova linha"
```
- O comando **echo "Adicionando nova linha" >> readme.txt** adiciona uma nova linha de texto ao final do arquivo readme.txt. Em seguida, git status mostra que o arquivo foi modificado, e **git diff** exibe as diferenças entre a versão atual e a anterior  ou seja, o que exatamente foi alterado. Depois, **git add readme.txt** coloca o arquivo modificado na área de preparação, e **git commit -m "Atualiza readme.txt com nova linha"** registra oficialmente essa atualização no histórico, com uma mensagem explicando a mudança.

> `git diff` mostra as diferenças entre a versão atual e a anterior.

---

## ♻️ 9. Desfazer mudanças

```bash
git restore readme.txt              # descarta mudanças não adicionadas
git restore --staged readme.txt     # remove da área de staging
```
- O comando **git restore readme.txt** descarta mudanças feitas no arquivo readme.txt que ainda não foram adicionadas com **git add**, voltando o arquivo à última versão salva no commit. Já o **git restore --staged readme.txt** remove o arquivo da área de preparação (staging), ou seja, desfaz o git add, mas mantém as alterações no arquivo. Isso é útil quando você adicionou algo por engano e quer revisar antes de confirmar.

> Ideal para corrigir erros antes de um commit.

---

## 🌿 10. Criar e alternar entre branches

```bash
git branch                         # lista branches
git branch nova_funcionalidade     # cria nova branch
git switch nova_funcionalidade     # muda para ela
```
- O comando **git branch** lista todas as branches existentes no repositório e mostra qual está ativa no momento (marcada com um asterisco). Já o **git branch nova_funcionalidade** cria uma nova branch chamada nova_funcionalidade, onde você pode desenvolver algo novo separadamente. Por fim, **git switch** nova_funcionalidade muda para essa branch, permitindo que você trabalhe nela sem afetar o código da branch principal (main).

> Cada branch é uma linha independente de desenvolvimento.

---

## 🧬 11. Fazer commits em outra branch

```bash
echo "Nova feature" > feature.txt
git add feature.txt
git commit -m "Adiciona nova feature"
```
-  O comando **echo "Nova feature" > feature.txt** cria um arquivo chamado feature.txt contendo o texto “Nova feature”. Em seguida, **git add feature.txt** adiciona esse arquivo à área de preparação, indicando que ele será incluído no próximo commit. Por fim, **git commit -m "Adiciona nova feature"** grava essa alteração no histórico do repositório, com uma mensagem explicando que uma nova funcionalidade foi adicionada.

---

## 🔀 12. Voltar e mesclar mudanças

```bash
git switch main
git merge nova_funcionalidade
```
- O comando **git switch main** faz você voltar para a branch principal (main), onde fica a versão estável do projeto. Depois, **git merge nova_funcionalidade** junta as alterações feitas na branch nova_funcionalidade com o conteúdo da main. Assim, todas as modificações e commits daquela branch são incorporados ao projeto principal, mantendo o histórico das mudanças.

> Junta as alterações da branch `nova_funcionalidade` na `main`.

---

## 🗑️ 13. Excluir branches locais

```bash
git branch -d nova_funcionalidade
```
- O **git branch -d nova_funcionalidade** remove a branch nova_funcionalidade do repositório local, mas apenas se todas as alterações dessa branch já tiverem sido incorporadas . É uma forma de manter o repositório organizado, eliminando branches que já cumpriram seu propósito.

---

## 🧹 14. Ignorar arquivos com `.gitignore`

Crie um arquivo chamado `.gitignore` e adicione:

```
*.log
*.tmp
node_modules/
```

Depois:

```bash
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```
-  Primeiro o arquivo **.gitignore** é criado para listar tipos de arquivos ou pastas que o Git deve ignorar.Depois, **git add .gitignore** adiciona o arquivo à área de preparação, e **git commit -m "Adiciona arquivo .gitignore"** registra essa adição no histórico do repositório. Isso evita que arquivos desnecessários poluam o controle de versão.

---

## 🧠 15. Visualizar informações úteis

```bash
git status
git log --oneline --graph --decorate
git diff
git show HEAD
```
- O **git status** mostra quais arquivos foram modificados, adicionados ou ainda não estão sendo rastreados, indicando o que precisa ser preparado ou comitado. O **git log --oneline --graph --decorate** exibe o histórico de commits de forma resumida, mostrando a estrutura de branches como um gráfico e destacando nomes de branches ou tags. Já o **git diff** mostra as diferenças entre os arquivos atuais e a última versão confirmada, permitindo ver exatamente o que foi alterado. Por fim, **git show HEAD** exibe detalhes do último commit, incluindo a mensagem e as alterações feitas nos arquivos, oferecendo uma visão completa do que aconteceu no repositório.

> `--graph` mostra o histórico com ramificações visualmente.

---

## 💡 16. Exemplo de fluxo completo

```bash
git init
echo "Aula prática Git local" > readme.txt
git add .
git commit -m "Primeiro commit"
git branch dev
git switch dev
echo "Nova versão em desenvolvimento" >> readme.txt
git add .
git commit -m "Atualiza versão dev"
git switch main
git merge dev
git log --oneline --graph
```

---

## 📘 Créditos

Material criado para fins educacionais na aula prática de **Git Local**,  
ministrada por *Anderson R. M. Gomes* 🧑‍🏫

---

**🚀 Próximos passos:**  
Na próxima aula, você aprenderá a conectar este repositório local ao GitHub com os comandos `git remote`, `git push` e `git pull`.
