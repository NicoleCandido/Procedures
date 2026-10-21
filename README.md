<h1 align="center">Stored Procedures no MySQL</h1>

<p align="center">
  <img src="https://img.shields.io/badge/MySQL-8a2be2?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL-ff69b4?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Concluído-8a2be2?style=for-the-badge" />
</p>

<p align="center">
  Conjunto de <b>stored procedures</b> para consultar e gerenciar um cadastro de países,<br>
  praticando parâmetros de entrada (<code>IN</code>) e de saída (<code>OUT</code>).
</p>

---

## Estrutura

```
Procedures/
├── procedures.sql   # Script completo do banco
└── README.md
```

## Modelo de dados

| Tabela | Campos                                        |
| :----- | :-------------------------------------------- |
| `Pais` | `id_pais` (PK, auto incremento), `nome_pais` (único) |

## Procedures

| Procedure                     | Parâmetro      | O que faz                                              |
| :---------------------------- | :------------- | :----------------------------------------------------- |
| `listar_paises(id)`           | `IN INT`       | Lista todos os países (`NULL`) ou um pelo id           |
| `contar_paises(@total)`       | `OUT INT`      | Conta os países e devolve o total em uma variável      |
| `selecionar_paises(qtd)`      | `IN INT`       | Mostra os primeiros N países em ordem alfabética       |
| `paises_com_letra(letra)`     | `IN CHAR(1)`   | Mostra os países que começam com a letra informada     |

### Exemplos de uso

```sql
CALL listar_paises(NULL);      -- todos os países
CALL listar_paises(2);         -- só o país de id 2

CALL contar_paises(@total);    -- guarda o total em @total
SELECT @total;                 -- mostra: 5

CALL selecionar_paises(3);     -- Argentina, Bolívia, Brasil
CALL paises_com_letra('B');    -- Bolívia, Brasil
```

## O que o script pratica

- Criação de procedures com `DELIMITER` e `BEGIN ... END`
- Parâmetros **`IN`** (entrada) e **`OUT`** (saída)
- Estrutura condicional `IF ... ELSE` dentro da procedure
- `COUNT ... INTO`, `LIMIT` e `LIKE` com `CONCAT`
- `DROP PROCEDURE IF EXISTS` para o script poder ser executado mais de uma vez
