# Anotações GIT
 

 ### Configurar nome de usuário e email no git

* git config --global user.name "xxxxxxxxx"


* git config --global user.email "xxxxxxx"


Caso eu tenha um arquivo no repositório do meu git, e eu não quero que ele seja commitado, eu deixo o nome dele como "nomedoarquivo".gitignore . Esse "gitignore" faz com que o arquivo seja ignorado pelo git

### Inicializar um repositório GIT na pasta local :
	
	git init

### Verificar status do git :
	
	git status

### Verificar na Stage Area :

	git status --show-stash

### Adicionar arquivos que não estão rastreados por nome:
	
	git add "nome do arquivo" 

### Adicionar arquivos que não estão rastreados por tipo :
	
	git add .txt("extensão do tipo de arquivo desejado")


### Adicionar todos os arquivos do repositório :
	
	git add

### Dar um commit no git :

	git commit

Ou

	git commit -m "Mensagem de texto" 

O de cima é preferível, pois você já insere ao que esse git está relacionado e pula uma etapa de pergunta do cmd.

Eu posso comittar sem eu ter que dar o "git add", mas não é aconselhável : 
	
	git commit -a -m

**Nota** : O "-a" faz com que o commit ignore a etapa da "Stage" em área, faz com que as modificações sejam adicionadas automaticamente no commit. O "-m" é para colocar uma mensagem no commit;

Caso eu tenha feito um commit, porém há alterações que eu ainda precisava fazer em um dos arquivos e acabei esquecendo, ao invés de ter que fazer um novo commit, podemos unificar ele com o último que foi commitado. Dessa forma, o meu último commit é atualizado com os arquivos que faltavam, e o comentário que foi adicionado : 
	
	git commit --amend -m "Comentário" 



### Enviar alterções commitadas para o repositório remoto :

	git push

### Puxar alterações do repositório GITHUB :

	git pull

### Ver o que foi alterado no arquivo desde o último commit :
	
	git diff

Quando eu mando o arquivo alterado para minha "Stage area", o diff não vai mais me mostrar as diferenças do arquivo, pois eu acabei adicionando o arquivo modificado a minha "Stage area", porém, tem um comando o qual é possível fazer isso :

	git diff --staged

### Verificar os logs de commit :
	
	git log
**Nota** : Quando é mostrado o log, há um campo "commit" com uma chave, essa chave, nos permite retroceder o estado do projeto a versão de um especificado commit 

Verificar os comits com mais detalhes :
	
	git log -p

É possível adicionar um limite de logs, exemplo :
	
	git log -p -1 
	
	Nota: O -1, indica que vai trazer apenas o commit mais recente.

### Abrir a interface gráfica do git, para melhor visualização dos logs:

	gitk

Na hora que eu mando os arquivos para a Stage area, e havia um arquivo o qual não era para ser adicionado, eu posso retroceder a ação com o comando :

	git restore --staged <arquivo>
	
	OU ao invés de colocar o nome do arquivo, eu posso colocar o "." indicando todos, ou a extensão do arquivo

### Restauração de arquivo

Caso tenha sido feita muitas modificações em um arquivo, devido a testes, e não sabe mais direito o que foi alterado, é possível retornar o estado original do arquivo(desde o último commit) :

	git restore <arquivo> 

### Remover arquivos 

Quando faço alterações nos arquivos, e eu removo um arquivo que já havia sido commitado no repositório, para commitar as alterações que foram feitas, eu preciso remover os arquivos os quais deletei no git :

	git rm <arquivo>

## Tags do GIT

Para melhor identificação dos commits, podemos adicionar tags a eles, exemplo "versao 1.0" e coisas do tipo :

	git tag v1.0

	git tag -a 1.0 -m "Versao 1.0"

	git tag -a v1.0 <Chave do commit> -m "Tag da versão 1.0"

	Nota : Da segunda forma, é possível deixar alguma anotação na tag, que é o mais recomendado, da terceira forma, é possível criar uma tag em algum commit específico

## Voltar arquivos a uma versão específica

Para eu voltar a versão dos meus arquivos a alguma tag específica :

	git checkout <tag>
	git checkout master

	Nota : A segunda forma, volta ao meu branch master, que é onde eu terei o último commit validado

## Branchs

O que são branchs ? Eu tenho o branch master, que é a versão principal do meu projeto, e caso eu queira fazer testes, ou até mesmo for implementar uma nova função, para não ferrar com o ambiente de produção, eu posso criar um novo branch, para fazer esses testes. Então o branch é como o significado literal mesmo, o meu projeto é uma "árvore" e o master é o galho principal, e eu posso criar outros "galhos" no meu projeto.
	
	git branch <NomeDoGalho>
	git branch -d <NomeDoGalho>

	Nota : O segundo serve para apagar outro branch criado

Caso eu faça alterações em um branch, e precise colocar essas alterações no branch master, eu primeiro volto ao meu branch master, pois é necessário estar no branch desejado e informar o branch que deseja ser copiado: 
	
	git checkout master
	git merge <NomeDoGalho>

	Nota : O merge, é o que faz a copia, faz meio que a junção dos dois

Caso eu faça alterações em um arquivo no branch "teste", eu dê um commit, e mais tarde, faça alterações no mesmo arquivo e nas mesmas linhas que foram alteradas no branch "teste", no branch "master" e dê um commit, isso atrapalha caso seja necessário dar um merge do branch de "teste" para o "master". O mesmo acaba gerando conflitos. É gerado um texto no arquivo que foi detectado o conflito , e é preciso decidir qual parte eu quero manter, a de cima ou a de baixo:

	
	<<<<<<< HEAD
	Teste1
	=======
	funtion(hazard 1234!)
	>>>>>>> teste
	
## Gerar chaves SSH:

	ssh-keygen

Gerada a chave SSh e configurada em nosso GITHUB, é possível clonarmos projetos através de chaves SSH's

