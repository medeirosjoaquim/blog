---
layout: post
title: Trocar palavra em arquivo usando sed
description: Essa dica é ótima para refatorar
ou apenas para alterar arquivos em lote.
Use a linha de comando para trocar todas as ocorrências de uma palavra em um ou vários arquivos.
---

sed -i 's/original_word/new_word/' file.txt

sed -i -e 's/Read More/Leia Mais/g'

Com esse snippet você pode fazer um loop nos arquivos e, em cada um,
executar a substituição da palavra desejada.

 find . | while read -r file; do if test -f $file; then sed -i 's/escapeRoom/someHowAgain/' $file; else echo "Não é um arquivo"; fi; done

 Explicação: Usamos uma sequências de pipes (" | ") para criar um
 primeiro output com todos o conteúdo da pasta:
 ```
 find .
 ```

 Enviamos esse conteúdo para um loop while -r que cria a variável "file":

 ```
 while read -r file;
 ```

 Para cada resultado trazido pelo loop, testamos se o resultado é um arquivo e, se for, então (then, rs):

```
sed -i 's/escapeRoom/someHowAgain/' $file
```

Executamos nosso comandinho!
Use com cuidado para porque você vai alterar todas as ocorrências
em um ou vários arquivos. Se fizer uma alteração não desejada, encontre
o erro e repita o comando para corrigir!
