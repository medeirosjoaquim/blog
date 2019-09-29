---
title: Encontrar arquivo que possui 'string'
date: 2017-08-18
---

### Encontrando arquivo que possua determinada string

Quando estamos 'debugando' um código, é comum precisar encontrar quais arquivos
fazem referência a determinada função, método etc...

Com essa combinação de find + grep podemos listar rapidamente
quais arquivos contém determinada expressão

No exemplo, vamos procurar arquivos que façam referência
à 'ready_function'

```
find . -iname '*php' | xargs grep 'ready_function' -sl
```
