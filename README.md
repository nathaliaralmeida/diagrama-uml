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

    %% RELACIONAMENTOS BASEADOS NO MINI-MUNDO
    
    %% Requisito (h): Um paciente pode ter vários profissionais responsáveis (Médico, Enfermeiro, Terapeuta)
    Profissional "1..*" -- "0..*" Paciente : responsável por

    %% Requisito (c, d): O atendimento registra a ação do profissional no paciente
    Profissional "1" -- "0..*" Atendimento : realiza
    Paciente "1" -- "0..*" Atendimento : recebe

    %% Requisito (d): Cada atendimento consulta a tabela de repasse do ERP Versatilis
    Atendimento "0..*" -- "1" TabelaRepasse : utiliza

    %% Requisito (g): A avaliação é feita após o atendimento para medir o desempenho
    Atendimento "1" -- "0..1" Avaliacao : gera
