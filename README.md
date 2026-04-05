```mermaid
classDiagram
    %% Entidades Principais
    class Profissional {
        +int id_profissional
        +String nome
        +String registro_conselho
        +String especialidade
        +float percentual_repasse
        +consultarPacientes()
        +calcularRemuneracao(mes, ano)
    }

    class Paciente {
        +int id_paciente
        +String nome
        +DateTime data_admissao
        +String status_tratamento
        +getResponsaveis()
    }

    class Atendimento {
        +int id_atendimento
        +DateTime data_hora
        +String tipo_tratamento
        +String descricao
        +float valor_base
        +registrarAvaliacao(nota, comentario)
    }

    class Avaliacao {
        +int id_avaliacao
        +int nota_desempenho
        +String observacoes
    }

    class TabelaRepasse {
        +int id_item
        +String servico
        +float valor_referencia
    }

    %% Relacionamentos (Regras de Negócio)
    Profissional "1..*" -- "0..*" Paciente : acompanha >
    Profissional "1" -- "0..*" Atendimento : realiza >
    Paciente "1" -- "0..*" Atendimento : recebe >
    Atendimento "1" -- "0..1" Avaliacao : gera >
    Atendimento "0..*" -- "1" TabelaRepasse : baseia-se em >
