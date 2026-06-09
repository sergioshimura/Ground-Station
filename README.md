# Estação de Solo PTS — Parque Tecnológico de Sorocaba

Repositório de referência técnica para a implantação da **Estação Terrestre 4.0 para Nanosatélites** no Parque Tecnológico de Sorocaba (PTS), com financiamento FINEP (programa PTSINOVA40).

**Consultor responsável:** Prof. Dr. Sergio Shimura — IFSP Sorocaba  
**Colaborador:** Adolfo Carvalho — Doutorando em Astronomia, Caltech  
**Contato:** shimurasergio@gmail.com

---

## Contexto do Projeto

O PTS submeteu o projeto **PTSINOVA40** à FINEP em 28/03/2022 (total: R$ 14,24M, 22 meses, 6 componentes). A **Estação Terrestre 4.0** é um dos 6 componentes, com parceria declarada com a **Alya Nanosatellites Constellation** (Toulouse, França).

- **Orçamento aprovado para equipamentos:** R$ 187.209,60
- **Orçamento para consultoria (Meta 3 FINEP):** R$ 90.000
- **Espaço físico:** sala de 56,72 m²
- **Meta de impacto:** capacitação de 30 jovens/ano

---

## Orçamento Aprovado (R$ 187.209,60)

| Linha | Valor Aprovado | Equipamento Recomendado |
|---|---|---|
| Antenas VHF/UHF | R$ 10.290 | 4× Yagi cruzada (2× VHF 137 MHz + 2× UHF 435 MHz) |
| RF Receptor | R$ 35.494 | Ettus USRP B210 (70 MHz–6 GHz, USB3) |
| RF Análise | R$ 11.735 | TinySA Ultra + antena L-band (patch 1,694 GHz p/ GOES-16) |
| RF Amplificação | R$ 53.585 | LNA 137+435 MHz+L-band + filtros + cabeamento LMR-400 |
| Controle e Movimento | R$ 54.983 | SPID RAS Az/El + controlador + interface PC |
| 4× Monitor 30" | R$ 9.720 | Conforme aprovado |
| **Total** | **R$ 187.209,60** | |

> **Atenção:** Computadores/workstations não constam da lista aprovada (apenas monitores). Necessário verificar se estão em outra linha da Meta 2 ou solicitar inclusão.

---

## Satélites Operacionais com a Configuração Aprovada

### VHF/UHF (antenas Yagi — aprovadas)

| Satélite/Sinal | Frequência | O que recebe |
|---|---|---|
| NOAA 15/18/19 APT | 137,5 / 137,62 / 137,1 MHz | Imagens meteorológicas 4 km/pixel |
| Meteor-M N2-3 LRPT | 137,9 MHz | Imagens meteorológicas ~1 km/pixel |
| ISS APRS beacon | 145,825 MHz | Telemetria + SSTV periódico |
| CubeSats LEO (TinyGS) | 433–437 MHz | Telemetria educacional |
| FOSSASAT-2E (uplink/downlink) | 437,525 MHz | Dados de sensores IoT |

### L-band (add-on: patch + LNA, ~R$ 4–8k)

| Satélite/Sinal | Frequência | O que recebe |
|---|---|---|
| GOES-16 LRIT | 1.694 MHz | Imagens América do Sul, 10 min/ciclo, 500m–2km/pixel |
| NOAA HRPT | 1.698–1.707 MHz | Imagens 1,1 km/pixel |

> GOES-16 é geoestacionário a 75,2°W — elevação ~55° em Sorocaba. Sinal aberto e gratuito.

---

## Escopo da Consultoria de Sergio Shimura

### Incluído (4 fases do NanosatélitesConsultoria.pdf)

**Fase 1 — Diagnóstico e Dimensionamento (jun/2026)**
- Levantamento técnico da infraestrutura existente
- Especificação técnica das antenas (tipo, ganho, polarização)
- Especificação do sistema RF (receptor, amplificadores, filtros)

**Fase 2 — Projeto Executivo de Sistemas e IoT (jul–ago/2026)**
- Integração de dados IoT (sensores LoRa, protocolos)
- Arquitetura de visualização (dashboard, sala de controle)
- Protocolo de criptografia e segurança de dados

**Fase 3 — Gestão de Aquisições e Suporte Técnico (set–out/2026)**
- Caderno de encargos para licitação
- Avaliação técnica de fornecedores
- Coordenação com parceiros (Alya Nanosatellites, INPE, Caltech)

**Fase 4 — Treinamento e Transferência de Tecnologia (out–nov/2026)**
- Capacitação operacional da equipe PTS
- Manual de operação da estação

### Excluído do Escopo

- Projetos civis e elétricos (estrutura de fixação de antenas, SPDA, instalações elétricas) — requer engenheiro civil/elétrico com ART
- Obtenção de licenças regulatórias (ANATEL, Prefeitura, Corpo de Bombeiros, ANAC)
- Homologação e importação de equipamentos RF
- Negociação e assinatura de contratos comerciais com fornecedores
- Implementação de criptografia e segurança de dados

---

## Cronograma Jun–Nov/2026

| Mês | Fase | Entregável Principal |
|---|---|---|
| Jun/2026 | Fase 1: Diagnóstico e Dimensionamento | Relatório de viabilidade + Documento RF |
| Jul/2026 | Fases 1+2: Infraestrutura e Sistemas | Projeto estrutural antenas + Plano IoT |
| Ago/2026 | Fases 2+3: Sistemas e Aquisições | Projeto Sala de Controle + Protocolos |
| Set/2026 | Fase 3: Gestão de Aquisições | Caderno de licitação + Draft Manual |
| Out/2026 | Fases 3+4: Suporte e Treinamento | Pareceres fornecedores + Manual + Treinamento |
| Nov/2026 | Encerramento e Inauguração | Estação operacional inaugurada + Relatório final |

---

## Parcerias Estratégicas

| Parceiro | Área | Relevância |
|---|---|---|
| Alya Nanosatellites (França) | Nanosatélites comerciais | Parceiro original do projeto FINEP 2022 — reativar |
| INPE (São José dos Campos) | CubeSat-BR, meteorologia | Programa nacional de CubeSats |
| Caltech/JPL (via Adolfo Carvalho) | Radioastronomia, ALMA | Conexão estratégica para Etapa 3 |
| Morehead State University (EUA) | Estação universitária CubeSats | Referência mundial |
| Libre Space Foundation / SatNOGS | Rede open-source global | Integração operacional imediata |
| AMSAT-BR | Satélites amadores | Comunidade ativa no Brasil |
| FATEC Sorocaba / IFSP Sorocaba | Ensino técnico | Parceiros locais do PTS |

---

## Licenciamento e Regulação

| Órgão | O que é necessário | Prazo típico |
|---|---|---|
| ANATEL | Homologação dos equipamentos (fabricante) + Licença de Estação + Autorização de Uso de RF (se uplink) | Meses |
| Prefeitura | Alvará de construção para estrutura de antenas + ART CREA | Semanas–meses |
| Corpo de Bombeiros | AVCB atualizado para o laboratório | Semanas |
| ANAC | Verificar restrição de altura (Aeroporto Bertram Luiz Leupolz) | Consulta prévia |

> **Distinção crítica:** estação **só receptora** (SDR/TinyGS) tem exigências muito menores que estação com **uplink** (controle de satélites). O FINEP cita controle — PTS precisa decidir antes de iniciar o licenciamento.

---

## Plano em 3 Etapas (proposta Sergio para Adolfo Carvalho)

1. **Etapa 1 (até nov/2026):** implantação da estação de solo — antenas, amplificadores, receptor, computadores, capturando dados de satélites meteorológicos e IoT
2. **Etapa 2:** cursos, workshops e sensor IoT próprio recebido via satélite (loop completo demonstrado com alunos)
3. **Etapa 3:** desenvolvimento de satélite próprio — requer edital separado (CubeSat custa US$ 50k–300k)

---

## Referências

- `NanosatélitesConsultoria.pdf` — caderno de escopo da Inova Sorocaba (mar/2026)
- `formulario FINAL 28032022.pdf` — formulário FINEP PTSINOVA40 (2022)
- `Parecer_Tecnico_EstacaoSolo_SergioShimura.docx` — parecer técnico (20/05/2026)
- `Proposta Estação de Solo-Shimura.pptx` — proposta de consultoria (jun/2026)
- ISISPACE Ground Station Datasheet — referência de equipamentos profissionais (TU Delft spin-off)
