# git-study <img align="center" src="https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white" alt="Git Badge">

Olá, seja bem-vindo ao meu repositório de estudo sobre GIT, onde eu documento por meio deste _README_ comandos que antes eram desconhecidos por mim ou pouco aprofundados e que podem ajudar a resolver situações críticas no cotidiano como desenvolvedor.

## Comandos GIT 💡

### 1. Descartar alterações realizadas

Situação: Após clonar um repositório e realizar modificações nele, mudou de ideia e quer voltar ao estado original do último commit.

**Sequência de comandos:** 

- ```git reset``` (tira tudo que está no stage (adicionado para ser commitado) e volta para a área de alterações não rastreadas)
- ```git clean -df``` (remove todos os arquivos e diretórios criados)
- ```git checkout -- .``` (restaura todas as deleções de arquivos e todas as modificações realizadas nos arquivos que estão em stage)

### 2. Visualizar log dos commits do projeto

Situação: Você deseja ver o log dos commits de um projeto.

**Comando:** ```git log ou git log --oneline``` (exibem no terminal mais informações sobre os commits e o código de cada um deles. A versão com --oneline mostra os dados de maneira mais resumida)

### 3. Excluir um commit indesejado do repositório local

Situação: Após realizar um commit indesejado, você deseja apagar um ou mais commits que foram feitos no projeto.

**Comando:** ```git reset --hard <idCommit>``` (deleta todos os commits que foram feitos posteriormente ao commit informado e torna ele o HEAD)

### 4. Excluir um commit indesejado do repositório remoto

Situação: Após deletar commits do repositório local, existe a necessidade de deletar os mesmos commits do repositório remoto.

**Comando:** ```git push origin HEAD --force``` ou ```git push -f``` (obriga a tornar o head do repositório remoto para o mesmo que está localmente)

### 5. Sincronizando repositório local com o remoto

Situação: Você está trabalhando em um repositório que vários desenvolvedores fazem atualizações sobre o código e precisa atualizar seu repositório local para que fique igual ao repositório remoto.

**Comando:** ```git pull origin <nomeBranch>``` (busca "o que está diferente" do repositório remoto e realiza alterações no repositório local para torná-los iguais)

### 6. Visualizando qual o destino do repositório local

Situação: Você precisa visualizar qual o repositório git que seu projeto local está vinculado.

**Comando:** ``git remote -v`` (exibe no terminal quais os remotes associados ao projeto local)

### 7. Adicionando um destino para novo repositório local

Situação: Você precisa adicionar um novo vínculo de repositório remoto com a sua máquina/projeto local.

**Comando:** ```git remote add origin <urlRepositorio.git>``` (vincula o repositório local com o repositório remoto criado)

### 8. Trocando o destino do repositório local

Situação: Existe a necessidade de trocar o repositório remoto associado ao projeto local.

**Comando:** ``git remote set-url origin <urlRepositorio.git>`` (troca a referência do origin, 'apontando' para a nova url informada)

### 9. Removendo temporariamente modificações realizadas

Situação: É necessário remover temporariamente modificações realizadas no código. Estas modificações não podem ser descartadas mas ainda não podem ser commitadas, pois não estão finalizadas. Suponha que foi iniciado o desenvolvimento de uma nova funcionalidade e surge a necessidade de fazer um pull para obter localmente a versão mais atualizada do projeto, ou de fazer um push dos commits locais sem enviar o código que ainda nao está pronto.

**Comando:** ``git stash`` (move as alterações não salvas para um lugar seguro denominado 'stash', as alterações podem ser resgatadas dessa área com o comando ``git stash apply``)

### Restaurando trabalho excluído 🔙

Após excluir acidentalmente um commit ou uma branch, você pode usar o comando `git reflog` para encontrar o código (id) do commit perdido. 

Passos:

- Identifique o código do commit excluído com ``git reflog``;
- Volte para o commit perdido com ``git checkout <idCommitExcluido>``;
- Crie uma nova branch a partir deste commit: ``git checkout -b <branchNova>``;
- Retorne para a branch principal utilizando ``git checkout main (ou master)``;
- Execute o merge com o comando ``git merge <nomeBranchNova>``.

Após executar os passos acima, os arquivos que antes estavam perdidos estarão na branch principal.

### Resolvendo conflito de merge 🧠

Contexto: Foi realizada modificações no repositório remoto no arquivo X, mas na sua máquina local este mesmo o arquivo X está desatualizado. Caso realize edições localmente no mesmo arquivo X o git irá "se perder", pois não saberá qual versão deverá manter: a que você estaria prestes a enviar ou a que já existe no repositório remoto.

**O que fazer?**

É preciso realizar sinalizar ao git qual versão do arquivo é a 'certa' a ser commitada. Fazemos isso excluindo o trecho de código indesejado e mantendo o novo código (**Incoming Change**, fruto das alterações realizadas localmente ou **Current Change**, que é a versão do arquivo presente no repositório remoto).
![teste](./imagens/image.png)
Após realizar as novas modificações, é possível adicioná-las com ``git add <nomeArquivo> ou .``, commitá-las com ``git commit -m <nomeBranch>`` e salvar as alterações em seu repositório remoto com ``git push``. O conflito de merge **não deve acontecer**.
