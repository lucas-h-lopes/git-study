# git-study <img align="center" src="https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white" alt="Git Badge">

Olá, seja bem-vindo ao meu repositório de estudo sobre GIT, onde eu documento por meio deste _README_ comandos que antes eram desconhecidos por mim ou pouco aprofundados e que podem ajudar a resolver situações críticas no cotidiano como desenvolvedor.

### Comandos GIT

Situação: Após clonar um repositório e realizar modificações nele, mudou de ideia e quer voltar ao estado original do último commit.

**Sequência de comandos:**

- ```git reset``` (tira tudo que está no stage (adicionado para ser commitado) e volta para a área de alterações não rastreadas)
- ```git clean -df``` (remove todos os arquivos e diretórios criados)
- ```git checkout -- .``` (restaura todas as deleções de arquivos e todas as modificações realizadas nos arquivos que estão em stage)

Situação: Você deseja ver o log dos commits de um projeto.

**Comando:** ```git log ou git log --oneline``` (exibem no terminal mais informações sobre os commits e o código de cada um deles. A versão com --oneline mostra os dados de maneira mais resumida)

Situação: Após realizar um commit indesejado, você deseja apagar um ou mais commits que foram feitos no projeto.

⚠️ **ATENÇÃO:** Esta ação é __irreversível__, ou seja, depois de realizada o commit não poderá ser restaurado a não ser que esteja salvo no repositório remoto.

**Comando:** ```git reset --hard <idCommit>``` (deleta todos os commits que foram feitos posteriormente ao commit informado e torna ele o HEAD)

Situação: Após deletar commits do repositório local, existe a necessidade de deletar os mesmos commits do repositório remoto.

⚠️ **ATENÇÃO:** Ao deletar os commits do repositório remoto, não será possível recuperar os arquivos dos commits excluídos.

**Comando:** ```git push origin HEAD --force``` (obriga a tornar o head do repositório remoto para o mesmo que está localmente)

Situação: Você está trabalhando em um repositório que vários desenvolvedorem sobem atualizações sobre o código e precisa atualizar seu repositório local para que fica igual como está no repositório remoto.

**Comando:** 
git pull origin <nomeBranch>
 (busca "o que está diferente" do repositório remoto e realiza alterações no repositório local para torná--los iguais)