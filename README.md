# Diagrama UML - Clínica de Reabilitação Saint Germain

```mermaid
classDiagram
    class Profissional {
        +int id
        +String nome
        +String especialidade
        +String crm
        +String coren
        +float taxa_base
        +gerarRelacaoPacientes() 
        +calcularPagamentoMensal()
    }

    class Paciente {
        +int id
        +String nome
        +Date data_nascimento
        +Date data_admissao
        +String status
        +calcularTempoTratamento()
    }

    class Atendimento {
        +int id
        +Date data_atendimento
        +Time hora
        +String descricao
        +float valor_base
        +obterDiaSemana()
    }

    class Tratamento {
        +int id
        +String nome_tratamento
        +String categoria
    }

    class Avaliacao {
        +int id
        +int nota_desempenho
        +String comentario_evolucao
    }

    class TabelaRepasse {
        +int id_tratamento
        +float valor_repasse
        +Date vigencia
    }

    %% RELACIONAMENTOS REAIS DO MINI-MUNDO
    
    %% h) Um profissional é responsável por um conjunto de pacientes (1:N)
    Profissional "1" -- "0..*" Paciente : é responsável por

    %% a, b, c) Atendimentos ligam Profissional e Paciente
    Profissional "1" -- "0..*" Atendimento : realiza
    Paciente "1" -- "0..*" Atendimento : recebe

    %% e) Atendimentos utilizam tratamentos específicos
    Atendimento "0..*" -- "1" Tratamento : executa

    %% d) Tabela de repasse define valores por tratamento
    Tratamento "1" -- "1" TabelaRepasse : define valor de

    %% g) Avaliação é registrada ao final de cada atendimento
    Atendimento "1" -- "0..1" Avaliacao : gera
