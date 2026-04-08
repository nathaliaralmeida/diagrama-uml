```mermaid
classDiagram
    class Profissional {
        +int id_profissional
        +String nome
        +String registro_conselho
        +String especialidade
        +float percentual_repasse
        +relacionarPacientes()
        +getDesempenho()
    }

    class Paciente {
        +int id_paciente
        +String nome
        +DateTime data_admissao
        +DateTime data_alta
        +String status
        +calcularTempoTratamento()
    }

    class Atendimento {
        +int id_atendimento
        +DateTime data_hora
        +String tipo_tratamento
        +float valor_total
        +String observacoes
    }

    class Avaliacao {
        +int id_avaliacao
        +int nota_desempenho
        +String feedback_paciente
    }

    class TabelaRepasse {
        +int id_item
        +String descricao_servico
        +float valor_base
    }

 
