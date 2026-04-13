```mermaid
classDiagram
    class GeradorAgenda {
        +String unidade
        +String predio
        +String sala
        +String especialidade
        +Date data_inicial
        +Date data_final
        +Time hora_inicial
        +Time hora_final
        +int tempo_minutos
        +String periodicidade
        +boolean check_segunda
        +boolean check_terca
        +boolean check_quarta
        +boolean check_quinta
        +boolean check_sexta
        +boolean check_sabado
        +boolean check_domingo
        +boolean verificar_choque
        +boolean exibir_web
        +gerarAgenda()
    }

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

    %% RELACIONAMENTOS

    Profissional "1" -- "0..*" GeradorAgenda : configura
    GeradorAgenda "1" -- "0..*" Atendimento : gera

    Profissional "1..*" -- "0..*" Paciente : responsável por

    Profissional "1" -- "0..*" Atendimento : realiza
    Paciente "1" -- "0..*" Atendimento : recebe

    Atendimento "0..*" -- "1" TabelaRepasse : utiliza

    Atendimento "1" -- "0..1" Avaliacao : gera
