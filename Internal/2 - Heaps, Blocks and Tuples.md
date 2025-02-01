---
aliases: 
tags: 
date created: Tuesday, January 28th 2025, 9:56:56 am
date modified: Tuesday, January 28th 2025, 10:42:48 am
---
Heap: Arquivo que contém todos os dados (rows) de nossa tabela.

Tuple ou Item: Linha individual da tabela.

Block ou Page: O arquivo heap que é divido entre muitos blocos diferentes ou paginas. Cada página/bloco guarda alguma quantidade de linhas (rows).

PS: Um arquivo HEAP não é relacionado diretamente a estrutura de dados HEAP.

---

Nessa imagem ilustra bem um HEAP arquivo, onde cada vez que ele acumula 8kb ele se segmenta em arquivos ainda menores.

![[Pasted image 20250128102822.png]]

---

Você pode obter mais informações sobre isso aqui:
https://www.linkedin.com/pulse/decoding-postgres-deep-dive-database-internals-prasenjit-sutradhar-e2x6c/

Ou um resumo da LLM:

1. **Estrutura de um Bloco**:
    
    - **Cabeçalho (Início)**: Contém metadados sobre o bloco.
    - **Dados Reais (Meio)**: Informações sobre onde os tuples estão localizados no bloco, mas não os dados em si.
    - **Espaço Livre (Meio)**: Área não utilizada que pode ser preenchida com novos dados.
    - **Dados Finais (Fim)**: Contém os tuples (linhas) reais da tabela.