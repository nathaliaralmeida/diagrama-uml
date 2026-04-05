# Projeto Clínica Saint Germain

```mermaid
classDiagram
    class Profissional {
        +int id
        +String nome
        +String especialidade
    }
    class Paciente {
        +int id
        +String nome
        +Date dataAdmissao
    }
    class Atendimento {
        +int id
        +DateTime dataHora
    }
    class Tratamento {
        +int id
        +String nomeTratamento
    }
    class Avaliacao {
        +int id
        +int notaEvolucao
    }

    Profissional "1" -- "0..*" Atendimento
    Paciente "1" -- "0..*" Atendimento
    Profissional "1..*" -- "0..*" Paciente
    Atendimento "1" -- "1" Tratamento
    Atendimento "1" -- "0..1" Avaliacao
