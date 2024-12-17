---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 6:58:23 pm
date modified: sexta-feira, dezembro 13º 2024, 7:00:08 pm
---
É o mesmo principio de UPDATE, por DELETAR ser algo perigoso é sempre bom certificar que ele acompanhar o WHERE, e dentro de WHERE tenha todas as clausulas necessárias para que somente os ELEMENTOS realmente em especifico sejam deletados.

É também interessante implementar dentro do banco de dados SOFT DELETE, ao qual impede que de fato exista deleções reais dentro do banco de dados assim mantendo os dados passíveis de auditoria.