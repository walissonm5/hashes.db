# hashes.db
banco de dados,para testes hash

# Hashes Database

Este projeto fornece uma implementação de um banco de dados SQLite para armazenar hashes de dados e arquivos PCAP. Ele também inclui funcionalidades para calcular e armazenar hashes usando diferentes algoritmos, bem como para incrementar automaticamente a versão do banco de dados cada vez que uma nova entrada é adicionada.

## Funcionalidades

- Armazenamento de hashes de dados com suporte a múltiplos algoritmos de hash (default `sha256`).
- Armazenamento de arquivos PCAP com cálculo e armazenamento de hashes.
- Incremento automático da versão do banco de dados.
- Commit automático da versão do banco de dados no repositório Git.

## Estrutura do Banco de Dados

O banco de dados SQLite contém duas tabelas principais:

### Tabela `valid_hashes`

| Campo       | Tipo       | Descrição                                   |
|-------------|------------|---------------------------------------------|
| id          | INTEGER    | Chave primária, autoincremento              |
| data        | TEXT       | Dados originais                             |
| hash_value  | TEXT       | Hash dos dados                              |
| algorithm   | TEXT       | Algoritmo usado para calcular o hash        |
| created_at  | DATETIME   | Data e hora de criação                      |

### Tabela `pcap_data`

| Campo       | Tipo       | Descrição                                   |
|-------------|------------|---------------------------------------------|
| id          | INTEGER    | Chave primária, autoincremento              |
| pcap        | BLOB       | Dados do arquivo PCAP                       |
| hash_value  | TEXT       | Hash do arquivo PCAP                        |
| created_at  | DATETIME   | Data e hora de criação                      |

## Utilização

### Inserir um Hash de Dados

Para inserir um hash de dados no banco de dados, use a função `inserir_hash`:

```python
hash_calculado = inserir_hash('meus_dados')
print(f"Hash calculado: {hash_calculado}")
```

### Inserir um Arquivo PCAP

Para inserir um arquivo PCAP no banco de dados, use a função `inserir_pcap`:

```python
hash_pcap = inserir_pcap('caminho/para/o/arquivo.pcap')
print(f"Hash do arquivo PCAP: {hash_pcap}")
```

## Requisitos

- Python 3.x
- Biblioteca `sqlite3` do Python
- Biblioteca `hashlib` do Python

## Como Executar

1. Clone o repositório:

```sh
git clone https://github.com/seu-usuario/hashes-db.git
cd hashes-db
```

2. Crie e ative um ambiente virtual:

```sh
python -m venv venv
source venv/bin/activate  # No Windows use `venv\Scripts\activate`
```

3. Execute o script Python:

```sh
python hashes_db.py
```

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir um pull request ou relatar um problema.

## Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
