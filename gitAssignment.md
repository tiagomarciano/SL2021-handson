# Git Assignment

**INDIVIDUAL**

**Entrega**: 23-Mar-21

Copie o arquivo em um repositorio que seja seu e coloque as respostas nas caixas abaixo
Abra uma issue nesse repositório aqui indicando o link para o arquivo no seu repo.

### Entenda o repositorio
Baixe o arquivo [handson.zip] (handson.zip) e descompacte-o
A pasta handson é um repositório git. Usando a linha de comando, altere o diretório para "handson/"


As caixas vazias
```

```
representam o conteúdo que você precisa preencher e postar em seu repositório privado

1. Descreva qual é a saída dos seguintes comandos
    -  `git branch` 
    -  `git checkout BRANCH_NAME` (USE THE NAME OF AN EXISTING BRANCH)
    -  `git log --decorate`

```
$ git branch
  feature-foo
* master

(o comando git branch pode ser usado para criar, listar e excluir branches)

$ git checkout feature-foo
Switched to branch 'feature-foo'

(o comando git checkout é usado para alternar de um branch para outro)

$ git log --decorate
commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:29:22 2018 -0700

    Adding header of method foo()

commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:27:16 2018 -0700

    Adding class A skeleton

commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Fri Aug 24 15:26:44 2018 -0700

    Creating all files (all empty)

(o comando git log exibe o log de commits, o sinalizador --decorate mostra todas as referências que apontam cada comimit)

```

2. Tente usar `git log --graph --all`. O que acontece?
```
$ git log --graph --all
* commit f67f266cf420735187053f10d32e2c0f7cbc5a43 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:30:05 2018 -0700
|
|     Adding class B skeleton
|
| * commit a70a8e9d3c5390e367028faf033f2a9ef03d2e91 (HEAD -> feature-foo)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Fri Aug 24 15:29:22 2018 -0700
|
|       Adding header of method foo()
|
* commit 309b0d73ff9c2163591c9e96e307fe61b4c8f58a
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Fri Aug 24 15:27:16 2018 -0700
|
|     Adding class A skeleton
|
* commit 9c1eeb8901b0926ce7fa13cc6ce0a1876fc4179b
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Fri Aug 24 15:26:44 2018 -0700

      Creating all files (all empty)

(o comando git log --graph --all exibe uma espécia de árvore de trabalho, o último commit realizado no master, o segundo commit realizado no branch feature-foo indo para direita ficando atrás da árvore do master que continua seu caminho, e outros dois commits)

```

3. Use `git diff BRANCH_NAME`  para ver as diferenças de um ramo e do ramo atual.
   Sumarize as diferenças do master e do outro ramo.

```
$ git diff master
diff --git a/A.java b/A.java
index 3ea227e..674b8ce 100644
--- a/A.java
+++ b/A.java
@@ -1,4 +1,7 @@
 public class A {
-
+
+   public void foo() {
+
+   }

 }
diff --git a/B.java b/B.java
index ae64e6b..e69de29 100644
--- a/B.java
+++ b/B.java
@@ -1,4 +0,0 @@
-public class B {
-
-
-}

(o comando git diff master exibe as mudanças em relação ao índice (área de preparação para o próximo commit))

$ git diff master..feature-foo
diff --git a/A.java b/A.java
index 3ea227e..674b8ce 100644
--- a/A.java
+++ b/A.java
@@ -1,4 +1,7 @@
 public class A {
-
+
+   public void foo() {
+
+   }

 }
diff --git a/B.java b/B.java
index ae64e6b..e69de29 100644
--- a/B.java
+++ b/B.java
@@ -1,4 +0,0 @@
-public class B {
-
-
-}

(o comando git diff master..feature-foo exibe o que foi modificado entre o branch master para o branch feature-foo)

$ git diff feature-foo..master
diff --git a/A.java b/A.java
index 674b8ce..3ea227e 100644
--- a/A.java
+++ b/A.java
@@ -1,7 +1,4 @@
 public class A {
-
-   public void foo() {
-
-   }
+

 }
diff --git a/B.java b/B.java
index e69de29..ae64e6b 100644
--- a/B.java
+++ b/B.java
@@ -0,0 +1,4 @@
+public class B {
+
+
+}

(o comando git diff feature-foo..master exibe o que foi modificado entre o feature-foo para o branch master)

```

4. Escreva uma sequencia de comandos para mesclar o ramo não-master no `master`

```
$ git checkout master
Switched to branch 'master'

$ git merge feature-foo
Merge made by the 'recursive' strategy.
 A.java | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)

```


5. Escreva um comando (ou sequência) para (i) criar um novo ramo chamado `math` (do` master`)
e (ii) mudar para este ramo

```
$ git checkout -b math
Switched to a new branch 'math'

```
   
6. Edite B.java adicionando o código abaixo ao conteúdo do arquivo
```java
System.out.println("I know math, look:")
System.out.println(2+2)
```

7. Escreva o comando (ou sequencia) para realizar o commit de suas mudanças
```
(modificando a origem do repositório)
$ git remote add origin git@github.com:tiagomarciano/SL2021-handson.git

(sequência de comandos para realizar o commit)
$ git add .
$ git status
On branch math
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   B.java
$ git commit -m 'Adding code in class B'
[math 485df43] Adding code in class B
 1 file changed, 2 insertions(+), 1 deletion(-)   

```

8. Volte para o branch `master` e mude B.java adicionando o seguinte código-fonte (confirme sua mudança para` master`):
```java
System.out.println("Hello World")

$ git checkout master
Switched to branch 'master'

(código-fonte de B.java alterado)

```

9. Escreva uma sequência de comando para mesclar o branch `math` em` master` e descreva o que aconteceu
```
$ git add .
$ git commit -m 'Adding code in class B - master'
[master d65d5cd] Adding code in class B - master
 1 file changed, 1 insertion(+), 1 deletion(-)
$ git merge math
Auto-merging B.java
CONFLICT (content): Merge conflict in B.java
Automatic merge failed; fix conflicts and then commit the result.

```
   
10. Escreva um conjunto de comandos para abortar a mesclagem
```
$ git merge --abort

```
   
11. Agora repita o item 9, mas prossiga com a mesclagem manual (Editando B.java). Todas as funções implementadas são necessárias. Explique o seu procedimento
```
$ git merge math
Auto-merging B.java
CONFLICT (content): Merge conflict in B.java
Automatic merge failed; fix conflicts and then commit the result.

$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   B.java

no changes added to commit (use "git add" and/or "git commit -a")

(Alterando o arquivo manualmente, removendo os marcadores de conflito)

public class B {
<<<<<<< HEAD
	System.out.println("Hello World")
=======
	System.out.println("I know math, look:")
	System.out.println(2+2)
>>>>>>> math

}

$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   B.java
$ git add .        
$ git commit -m "Merged and resolved the conflict in B.java"
[master 5f6a8e6] Merged and resolved the conflict in B.java

```

12. Escreva um comando (ou conjunto de comandos) para prosseguir com a mesclagem e atualizar o branch `master`
```
$ git push -u origin master
Warning: Permanently added the RSA host key for IP address '140.82.114.4' to the list of known hosts.
Enumerating objects: 23, done.
Counting objects: 100% (23/23), done.
Writing objects: 100% (23/23), 2.28 KiB | 291.00 KiB/s, done.
Total 23 (delta 0), reused 0 (delta 0)
To github.com:tiagomarciano/SL2021-handson.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```


