---
title: quick tip - Rename loop in bash
date: 2017-12-09
---

No exemplo, renomeando todos os nome.jpg para
nome_resize.jpg
```
$ ls

nome1.jpg
nome2.jpg
nome3.jpg
```
** Usando _for_ loop

$ for i in *.jpg; do mv -- $i  "${i/%.jpg/_resize.jpg}"; done

```
$ ls


nome1_resize.jpg
nome2_resize.jpg
nome3_resize.jpg
```

** O caminho inverso (echo para mostrar antes de fazer a troca):

```

for i in *.jpg; do  echo $i"${/%jpg/_resize}"; done

```

:)
