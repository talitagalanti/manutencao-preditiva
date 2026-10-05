# Dicionário de Dados — `manutencao_preditiva.csv`

**Origem:** base histórica de sensores do parque fabril, disponibilizada no Projeto Avaliativo do Módulo 1 (SENAI/SC). Descrição das colunas conforme as anotações do Departamento de Engenharia.

**Granularidade:** uma linha por registro de operação de equipamento.

**Local no projeto:** `data/raw/manutencao_preditiva.csv` (arquivo bruto, não deve ser editado).

## Colunas

| Coluna | Tipo | Unidade | Descrição |
|---|---|---|---|
| `udi` | inteiro | — | Identificador único de cada registro (1 a 10.000). |
| `id_produto` | texto | — | Código do produto: letra de qualidade + número de série. |
| `tipo` | categórico | — | Classe do equipamento pela especificação técnica: **L** (Low), **M** (Medium), **H** (High). |
| `temperatura_ar_k` | decimal | Kelvin | Temperatura do ambiente onde a máquina está instalada. |
| `temperatura_processo_k` | decimal | Kelvin | Temperatura gerada durante a operação do processo. |
| `velocidade_rotacao_rpm` | decimal | RPM | Velocidade de giro do motor. |
| `torque_nm` | decimal | N·m | Força de torção gerada pelo motor. |
| `desgaste_ferramenta_min` | inteiro | minutos | Tempo acumulado de uso da ferramenta de corte atual. |
| `falha_maquina` | binário | — | **Variável alvo (y).** 1 = falha mecânica; 0 = operação normal. |

## Colunas apenas para consulta (NÃO usar como preditoras)

As anotações da Engenharia informam que estas colunas registram o **motivo** da quebra. Elas só são conhecidas depois que a falha acontece. Por isso, usá-las em X causaria vazamento de dados (*data leakage*).

| Coluna | Descrição |
|---|---|
| `falha_twf` | Falha por desgaste da ferramenta (*Tool Wear Failure*). |
| `falha_hdf` | Falha por dissipação de calor / superaquecimento (*Heat Dissipation Failure*). |
| `falha_pwf` | Falha por falta ou excesso de potência elétrica (*Power Failure*). |
| `falha_osf` | Falha por esforço ou tensão mecânica excessiva (*Overstrain Failure*). |
| `falha_rnf` | Falha aleatória não detectada pelos sensores (*Random Failure*). |
