---
aliases: 
tags: 
date created: Tuesday, January 28th 2025, 9:40:30 am
date modified: Tuesday, January 28th 2025, 9:56:43 am
---
SHOW data_directory: Mostra o diretorio de armazenamento, onde o PostgreSQL guarda os dados.

Exemplo: User/sg/Library/Application Support/Postgres/var-12.

Dentro dessa raiz temos a seguinte configuração.

![[Pasted image 20250128094428.png]]

E dentro dessa pasta podemos adentrar a pasta base:
PS: Cada numero diferente é um banco diferente rodando dentro da sua máquina local.

SELECT oid, datname
FROM pg_database;

![[Pasted image 20250128094455.png]]

Dentro de cada pasta (banco de dados), podemos verificar que tem vários arquivos, e esses arquivos não são equivalente a quantidades de tabelas ou de rows em cada tabela, então a representação lógica do banco de dados não é a mesma usado pelo sequenciamento lógico humano.

SELECT * FROM pg_class;

Com isso podemos ter um entendimento melhor o que cada fragmento de arquivo significa dentro da pasta referente ao banco de dados.

---

No PostgreSQL, a interação entre os arquivos físicos e o software é gerenciada de forma a garantir a integridade, desempenho e consistência dos dados. Aqui está uma visão geral de como essa interação ocorre, com base na documentação do PostgreSQL:

### 1. **Estrutura De Diretórios e Arquivos**
   - **Data Directory**: Este é o diretório raiz onde o PostgreSQL armazena todos os dados relacionados ao cluster de banco de dados. O caminho para este diretório pode ser encontrado usando o comando `SHOW data_directory;`.
   - **Subdiretórios e Arquivos**: Dentro do diretório de dados, existem vários subdiretórios e arquivos que armazenam diferentes tipos de informações, como:
     - **base/**: Contém os arquivos de dados para cada banco de dados. Cada banco de dados tem uma subpasta identificada pelo OID (Object Identifier) do banco de dados.
     - **global/**: Armazena informações globais do cluster, como tabelas de sistema compartilhadas.
     - **pg_wal/**: Contém os arquivos de log de write-ahead logging (WAL), que são cruciais para a recuperação de falhas e replicação.
     - **pg_xact/**: Armazena informações sobre transações.

### 2. **Mapeamento De Bancos de Dados e Tabelas**
   - **OID (Object Identifier)**: Cada banco de dados e objeto dentro do PostgreSQL (como tabelas, índices, etc.) tem um OID único. O OID do banco de dados pode ser encontrado na tabela `pg_database`.
   - **pg_class**: Esta tabela de sistema contém informações sobre todas as tabelas, índices, sequências e outros objetos de banco de dados. Cada entrada nesta tabela tem um OID único que pode ser usado para mapear objetos lógicos para arquivos físicos.

### 3. **Arquivos Físicos e Blocos**
   - **Arquivos de Dados**: Cada tabela e índice é armazenado em um ou mais arquivos físicos dentro do diretório `base/`. O nome do arquivo geralmente corresponde ao OID da tabela ou índice. Se o arquivo crescer além de 1GB, ele será dividido em segmentos de 1GB, com um sufixo numérico (por exemplo, `12345`, `12345.1`, `12345.2`, etc.).
   - **Blocos (Pages)**: O PostgreSQL armazena dados em blocos de tamanho fixo (geralmente 8KB). Cada arquivo de dados é dividido em blocos, e cada bloco contém uma parte dos dados da tabela ou índice.

### 4. **Gerenciamento De Transações e WAL**
   - **Write-Ahead Logging (WAL)**: O PostgreSQL usa WAL para garantir a durabilidade e consistência dos dados. Todas as alterações são primeiro registradas nos arquivos WAL antes de serem aplicadas aos arquivos de dados. Isso permite a recuperação de falhas e suporta operações como replicação e point-in-time recovery.
   - **pg_xact**: Este diretório contém informações sobre o estado das transações, como quais transações estão em andamento ou foram commitadas.

### 5. **Operações De I/O**
   - **Leitura e Escrita**: O PostgreSQL gerencia operações de leitura e escrita nos arquivos físicos através de buffers em memória. O buffer cache é usado para reduzir a necessidade de leituras diretas do disco, melhorando o desempenho.
   - **Checkpoints**: Periodicamente, o PostgreSQL realiza checkpoints, onde todos os dados modificados no buffer cache são escritos nos arquivos de dados. Isso ajuda a garantir que os dados em disco estejam consistentes com o estado do banco de dados.

### 6. **Manutenção E VACUUM**
   - **VACUUM**: O PostgreSQL usa o comando `VACUUM` para limpar dados obsoletos e liberar espaço. Isso é importante para manter o desempenho e evitar o crescimento excessivo dos arquivos de dados.
   - **Autovacuum**: O PostgreSQL tem um processo chamado autovacuum que automaticamente executa operações de VACUUM e ANALYZE para manter o banco de dados otimizado.

### 7. **Backup E Restauração**
   - **Backup Físico**: Um backup físico envolve copiar diretamente os arquivos do diretório de dados. Isso pode ser feito enquanto o banco de dados está em execução, mas requer cuidado para garantir consistência.
   - **Backup Lógico**: Ferramentas como `pg_dump` e `pg_dumpall` permitem fazer backups lógicos, que são mais portáteis e podem ser restaurados em diferentes versões do PostgreSQL.