---
aliases: 
tags: 
date created: quarta-feira, janeiro 1º 2025, 5:52:28 am
date modified: quarta-feira, janeiro 1º 2025, 6:04:35 am
---
Podemos configurar restrições ao tentar efetuar deleções dentro de uma tabela, com isso podemos garantir consistência, integridade e lógica entre tabelas.

Por exemplo, podemos configurar a KEYWORD = ON DELETE RESTRICT, ao qual irá gerar um error ao tentar deletar algo corelacionado.

Tipos de ON DELETE:

- ON DELETE CASCADE
	- Quando algo é deletado na tabela pai, a tabela filha que tem dependencia é automaticamente deletada junta.
- ON DELETE SET NULL
	- Quando um registro é deletado na tabela pai, na tabela filha é setado na coluna com o mesmo ID com o valor nulo, útil para quando a tabela tem dependencia um/opcional para o pai.
- ON DELETE SET DEFAULT
	- Quando um registro é deletado na tabela pai, na tabela filha é setado/retornado para o valor default, lembrando que só é possível de utilizar essa constraint caso a coluna tenha um valor default pré configurado a priori.
- ON DELETE RESTRICT
	- Não permite que deleções no pai seja feita enquanto na tabela de dependencia tenha registros apontando para tabela pai, muito útil para situações onde algo realmente não pode ser deletado ou para processos de auditoria.
- ON DELETE NO ACTION
	- É igual ao restrict, mudando somente que essa validação para o final da transação, ou seja, se tabela B depende de A, e na tabela B temos referencia a LINHA 15 de tabela A, e essa linha 15 de A é deletada em conjunto na transacão, portanto se faz permitido de executar a deleção.