---
aliases: 
tags: 
date created: sexta-feira, dezembro 13º 2024, 6:52:51 pm
date modified: sexta-feira, dezembro 13º 2024, 6:58:04 pm
---
È sempre recomendável, sempre, sempre usar WHERE junto com clausulas UPDATE, isso se dá pois o UPDATE executa atualização de uma coluna com um valor somente para todas as ROWS, tendo somente exceção se incluido um WHERE em conjunto.

É adequado também que a IDE que você usa para operar o banco de dados te sinalizar quando um UPDATE sem WHERE está sendo executado.

E é sempre importante certificar que sua atualização vai atingir somente o que você quer, por exemplo, se você quer atualizar a população atual de Shangai da China, não use somente a validação por nome da cidade, mas sim o País desssa cidade também, evitando que a cidade indevida também seja atualizada em conjunto.