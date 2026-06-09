# Estação de Solo PTS — Parque Tecnológico de Sorocaba

Repositório de referência técnica para a implantação da **Estação Terrestre 4.0 para Nanosatélites** no Parque Tecnológico de Sorocaba (PTS), com financiamento FINEP (programa PTSINOVA40).

**Consultor responsável:** Prof. Dr. Sergio Shimura — IFSP Sorocaba  
**Colaborador:** Adolfo Carvalho — Dr. Astrofísica, Caltech; Pós-Doc em Harvard  
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
| Harvard/Caltech (via Adolfo Carvalho) | Astrofísica, ALMA, radioastronomia | Conexão estratégica para Etapa 3 |
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

### Documentos internos do projeto

- [QA_Sessoes.md](QA_Sessoes.md) — perguntas e respostas das sessões de consultoria técnica
- [NanosatélitesConsultoria.pdf](Referencias/NanosatélitesConsultoria.pdf) — caderno de escopo da Inova Sorocaba (mar/2026)
- [formulario FINAL 28032022.pdf](<Referencias/formulario FINAL 28032022.pdf>) — formulário FINEP PTSINOVA40 (2022)
- [Parecer_Tecnico_EstacaoSolo_SergioShimura.docx](Referencias/Parecer_Tecnico_EstacaoSolo_SergioShimura.docx) — parecer técnico (20/05/2026)
- [Proposta Estação de Solo-Shimura.pptx](<Referencias/Proposta Estação de Solo-Shimura.pptx>) — proposta de consultoria (jun/2026)
- [Parecer Técnico Estação de Solo para Satélites.eml](<Referencias/Parecer Técnico Estação de Solo para Satélites.eml>) — email de Mariane (26/05/2026) com lista FINEP

### Equipamentos e estações de referência

- [ISISPACE Ground Station (TU Delft spin-off)](https://www.isispace.nl/product/isis-ground-station/) — datasheet com specs completos de Yagi VHF/UHF e prato S-band
- [CubeSatShop — ISISPACE Ground Station](https://www.cubesatshop.com/product/isis-ground-station-system/) — mirror com preços e especificações
- [SatNOGS — Libre Space Foundation](https://satnogs.org) — rede global open-source de estações
- [Morehead State University Space Science Center](https://www.moreheadstate.edu/academics/colleges/science/csos) — referência mundial para estações universitárias

### Regulação

- [ANATEL — Regulamento Geral de Licenciamento](https://www.gov.br/anatel/pt-br/regulado/outorga/regulamento-geral-de-licenciamento) — estações receptoras dispensadas de licenciamento
- [ANATEL — Licenciamento Radioamador (COER)](https://www.gov.br/anatel/pt-br/regulado/outorga/radioamador-e-radio-cidadao/licenciamento-de-estacoes-do-radioamador) — necessário para uplink em frequências de radioamador

### Satélites e redes

- [TinyGS](https://tinygs.com) — rede global de estações ESP32 receptoras de satélites LoRa (gratuito)
- [TinyGS Web Installer](https://installer.tinygs.com) — flash do firmware sem programação
- [FOSSASAT-2 GitHub](https://github.com/FOSSASystems/FOSSASAT-2) — satélite PocketQube open-source com uplink LoRa livre
- [Lacuna Space + The Things Industries](https://www.thethingsindustries.com/news/lacuna-space-and-the-things-industries-partner-to-provide-free-access-to-direct-to-satellite-lora-connectivity-for-developers-around-the-world/) — free tier de conectividade LoRaWAN via satélite para desenvolvedores
- [NOAA Satellites — APT/HRPT](https://www.noaa.gov/satellites) — portal oficial NOAA com dados e frequências
- [GOES-16 — NOAA/NESDIS](https://www.nesdis.noaa.gov/current-satellite-missions/currently-flying/geostationary-satellites/goes-east) — satélite meteorológico geoestacionário cobrindo América do Sul
- [GOES-16 Open Data — AWS](https://registry.opendata.aws/noaa-goes/) — imagens públicas em tempo real na AWS

### Tutoriais IoT + LoRa + Satélite

- [RadioLib — biblioteca universal LoRa/FOSSASAT](https://github.com/jgromes/RadioLib) — suporte nativo ao protocolo FOSSASAT
- [Random Nerd Tutorials — ESP32 + LoRa RFM95](https://randomnerdtutorials.com/esp32-lora-rfm95-transceiver-arduino-ide/) — configuração básica no Arduino IDE
- [Random Nerd Tutorials — ESP32 + LoRa + Sensor + Web Server](https://randomnerdtutorials.com/esp32-lora-sensor-web-server/) — tutorial completo com sensor e servidor web
- [ESP32 Soil Moisture Sensor](https://esp32io.com/tutorials/esp32-soil-moisture-sensor) — leitura de sensor capacitivo de umidade do solo
- [FOSSASAT communication simulation (GitHub)](https://github.com/McOrts/fossasat1_satellite-communication-simulation) — simulação de comunicação bidirecional sem precisar esperar passagem de satélite
- [ESP32 LoRa Humidity + Temperature (GitHub)](https://github.com/rch-goldsnaker/esp32-lora-humidity-temperature) — projeto completo ESP32 + LoRa + sensores
- [RTL-SDR — Building a FossaSat-1 LoRa Ground Station](https://www.rtl-sdr.com/building-a-fossasat-1-lora-iot-ground-station/) — tutorial de estação receptora low-cost
