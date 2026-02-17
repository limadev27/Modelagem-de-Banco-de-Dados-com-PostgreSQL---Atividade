**Modelagem de Banco de Dados com PostgreSQL - Atividade**

## 📖 Apresentação do Projeto

O  Sistema de Registro de Atendimento  é um aplicativo desenvolvido para auxiliar empresas no controle de filas e no gerenciamento de atendimentos realizados diariamente. A aplicação permite organizar o fluxo de clientes, registrar atendentes, acompanhar o tempo de atendimento e manter um histórico completo das interações realizadas.

O principal objetivo do sistema é otimizar o processo de atendimento, reduzir falhas no controle manual e fornecer maior organização e eficiência operacional. Além disso, a ferramenta possibilita melhor acompanhamento administrativo, permitindo análise de desempenho e melhoria contínua dos serviços prestados.


```
erDiagram
    PESSOA {
        int id PK
        string nome
        string cpf
        string telefone
        string email
    }

    CLIENTE {
        int id PK
        int pessoa_id FK
    }

    ATENDENTE {
        int id PK
        int pessoa_id FK
        string setor
        string status
    }

    FILA {
        int id PK
        string nome
        string status
        date data
        int prioridade_id FK
    }

    PRIORIDADE {
        int id PK
        string descricao
    }

    ATENDIMENTO {
        int id PK
        datetime inicio
        datetime fim
        string status
        string observacoes
        int atendente_id FK
        int cliente_id FK
        int fila_id FK
    }

    PESSOA ||--|| CLIENTE : "pode ser"
    PESSOA ||--|| ATENDENTE : "pode ser"
    
    CLIENTE ||--o{ ATENDIMENTO : "recebe"
    ATENDENTE ||--o{ ATENDIMENTO : "realiza"
    
    FILA ||--o{ ATENDIMENTO : "organiza"
    PRIORIDADE ||--o{ FILA : "define"
```
