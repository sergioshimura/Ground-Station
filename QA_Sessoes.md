# Q&A — Estação de Solo PTS

Perguntas e respostas das sessões de consultoria técnica. Organizadas por tema.

---

## 1. Regulação e Licenciamento

### Q: Quais autorizações de órgãos a estação vai precisar (ANATEL, Bombeiros, Prefeitura, ANAC)?

**ANATEL:**
- **Homologação de equipamentos** — obrigação do fabricante/importador (não do PTS). Todo equipamento RF comercializado no Brasil já deve ter o Certificado de Homologação ANATEL. Verificar antes de comprar equipamentos importados.
- **Licença de Estação de Radiocomunicação** — necessário apenas se houver **transmissão**. Estação exclusivamente receptora é **dispensada de licenciamento** pela regulação ANATEL (veja Q abaixo).
- **Autorização de Uso de Radiofrequência** — obrigatório somente se houver **uplink** (transmissão para satélites).

**Prefeitura de Sorocaba:**
- Alvará de construção para a estrutura de fixação das antenas (mesmo dentro do PTS).
- ART do CREA (engenheiro civil responsável pela estrutura).

**Corpo de Bombeiros:**
- AVCB (Auto de Vistoria do Corpo de Bombeiros) atualizado para o espaço do laboratório.

**ANAC:**
- Verificar restrição de altura em relação ao Aeroporto Bertram Luiz Leupolz (Sorocaba). Consulta prévia antes de definir a altura do mastro/torre.

**Decisão crítica para o PTS:** o projeto FINEP menciona "controle de satélites" (uplink). Se a estação for apenas receptora (SDR, TinyGS), o licenciamento é muito mais simples. PTS precisa definir isso antes de iniciar o processo regulatório.

---

### Q: Para fazer uplink, a estação precisa de homologação ou certificação? Qual o termo correto?

Terminologia correta (ANATEL):

- **Homologação** = certificação do **equipamento** (obrigação do fabricante/importador, não do operador)
- **Licença de Estação de Radiocomunicação** = autorização para **instalar e operar** a estação
- **Autorização de Uso de Radiofrequência** = permissão para **usar determinada frequência** (obrigatório para uplink)

Para uplink de controle de satélites, o PTS precisaria de Licença de Estação + Autorização de RF. Para recepção pura, nenhuma licença de estação é necessária (veja Q abaixo).

---

### Q: Preciso de licença de estação de radiocomunicação se operar somente para recepção de sinais de satélite?

**Não.** Estações **exclusivamente receptoras são dispensadas de licenciamento** pela regulação ANATEL.

A lógica regulatória é clara: a ANATEL regula o **uso do espectro de radiofrequências**, e usar o espectro significa **transmitir**. Quem só recebe não ocupa o espectro — não precisa de licença de estação. O cadastramento voluntário no sistema Mosaico é possível (e dá proteção contra interferência), mas não é obrigatório.

**Resumo prático por configuração:**

| Configuração | Licença necessária? |
|---|---|
| SDR (RTL-SDR, USRP B210) + computador, só recepção | Não |
| TinyGS em ESP32, só recepção | Não |
| Antena Yagi + LNA + receptor NOAA/GOES-16 | Não |
| Uplink para satélite (qualquer transmissão) | Sim — Autorização de Uso de RF + Licença de Estação |
| Uplink em frequências de radioamador (ex: 437 MHz) | Sim — COER (Certificado de Operador de Estação de Radioamador) |

**Recomendação para o PTS:**
- **Etapa 1** (recepção pura: NOAA, GOES-16, CubeSats, TinyGS) — opera sem nenhuma licença de estação.
- **Futuro uplink** (ex: FOSSASAT-2E em 437 MHz) — o caminho mais simples é ter um pesquisador ou técnico com **licença de radioamador (COER)**. O processo é mais ágil que a licença comercial e cobre exatamente as frequências dos CubeSats educacionais.

> Fonte: Regulamento Geral de Licenciamento ANATEL — [gov.br/anatel](https://www.gov.br/anatel/pt-br/regulado/outorga/regulamento-geral-de-licenciamento)

---

## 2. Uplink para Satélites

### Q: Que tipo de comandos posso enviar para um satélite? Preciso de acordo de parceria?

**Tipos de comandos de uplink (do mais simples ao mais complexo):**

| Tipo | Exemplo | Restrição |
|---|---|---|
| Beacon request | Pedir que o satélite retransmita seu beacon | Protocolo aberto, sem acordo |
| Telemetria request | Solicitar dados de temperatura, tensão, etc. | Protocolo aberto na maioria dos CubeSats educacionais |
| Envio de mensagem/payload | Transmitir dados de sensores para o satélite armazenar | Requer acordo com o operador ou protocolo aberto (FOSSASAT) |
| Comandos de modo | Alterar modo de operação, ativar câmera, etc. | Restrito — requer parceria formal e chaves de autenticação |
| Comandos de controle de atitude | Alterar orientação do satélite | Exclusivo do operador — não disponível para terceiros |

**Acordos necessários:**
- Para **receber** telemetria: nenhum acordo — qualquer estação pode receber sinais de satélites em frequências abertas.
- Para **uplink de dados (payload):** registro no fórum/plataforma do operador (FOSSASAT exige registro; gratuito para fins acadêmicos).
- Para **uplink de controle:** Memorando de Entendimento (MoU) ou acordo de parceria formal com o operador. No caso da Alya Nanosatellites, reativar a parceria declarada no FINEP 2022.
- Para uso da rede **SatNOGS:** adesão à Libre Space Foundation (gratuito, open-source).

---

## 3. Estações de Referência na Europa (contexto Veritasium)

### Q: As estações em Amsterdam/Netherlands são governamentais ou privadas? Quais frequências rastreiam e para qual finalidade?

O vídeo do Veritasium (canal sobre ciência e engenharia) se refere às estações da **Universidade Técnica de Delft (TU Delft)** e seu spin-off comercial **ISISPACE**, em Delft, Países Baixos.

**Natureza:** universitária/privada — TU Delft é universidade pública holandesa; ISISPACE é empresa privada spin-off.

**Frequências e finalidades:**

| Banda | Frequência | Finalidade |
|---|---|---|
| VHF | ~137 MHz | Recepção de satélites meteorológicos (NOAA APT, Meteor) |
| UHF | 400–440 MHz | Telemetria de CubeSats LEO, FOSSASAT |
| S-band | 2–4 GHz | Downlink de dados de missões próprias (imagens, telemetria científica) |

**Finalidades principais:**
- Rastreamento de missões educacionais próprias (Delfi-C3, Delfi-n3Xt, Delfi-PQ)
- Suporte operacional a CubeSats de outras universidades
- Pesquisa em engenharia aeroespacial (ADCS, propulsão, comunicações)
- Treinamento de estudantes em operações de satélite

---

### Q: As estações da TU Delft têm antenas parabólicas de 3,2m e 4,0m?

**Não para VHF/UHF.** Antenas parabólicas grandes são usadas somente em S-band ou X-band.

**Configuração real da ISISPACE Ground Station (TU Delft spin-off):**

| Componente | Especificação |
|---|---|
| Antena VHF | Yagi 14 elementos, 3,2m de comprimento, ganho 12,34 dBic |
| Antena UHF | Yagi 30 elementos, 3,0m de comprimento, ganho 15,5 dBic |
| Antena S-band | Prato parabólico 2m (opcional), ganho 31,35 dBic |
| Rotor | Az/El, precisão 0,1°, suporta cargas >50 kg |
| Transceiver VHF | SDR-based, 100W |
| Transceiver UHF | SDR-based, 120W |
| Protocolo | AX.25 |
| Preço (VHF/UHF) | €99.500 |
| Preço (com S-band) | €139.500 |

**Conclusão:** antenas parabólicas de 3,2m e 4,0m **não são compatíveis com CubeSats LEO em VHF/UHF**. Para essas frequências, Yagis cruzadas são o padrão mundial (e o que a ISISPACE usa). Parabólicas grandes só fazem sentido em S-band ou X-band.

---

### Q: 4 antenas menores de ~3 m² cobrem a mesma área que uma antena de 4m (12 m²) e permitem redundância?

A matemática de área está correta: uma antena de 4m tem ~12,6 m² de área efetiva; 4 antenas de ~1,8m cada somam ~10 m².

**Porém há duas formas de combinar os sinais:**

| Modo | Ganho real | Complexidade | Custo |
|---|---|---|---|
| **Combinação coerente** (fase sincronizada, tipo ALMA) | = antena única equivalente | Altíssima — receptores com relógio atômico sincronizado | R$ 200k+ adicional |
| **Diversidade incoerente** (sem sincronismo) | +6 dB de margem de enlace (proteção contra efeito Doppler) | Baixa | Razoável |

**Recomendação:** 4 antenas menores em modo de diversidade incoerente são uma escolha válida para **Etapa 2/3**, não para a Etapa 1. Para VHF/UHF (137–437 MHz), Yagis cruzadas com bom rotator são mais eficientes e baratas do que arrays de dishes. Arrays de dishes fazem sentido em S-band ou X-band.

---

## 4. Imagens Meteorológicas via Satélite

### Q: Conseguiremos capturar imagens meteorológicas de amplo espectro e espectro visível? Qual a resolução? Quais tipos de análises serão possíveis?

**Sinais acessíveis com a configuração aprovada (VHF/UHF + L-band add-on):**

| Satélite | Sinal | Bandas | Resolução | Antena |
|---|---|---|---|---|
| NOAA 15/18/19 | APT | Visível + IR | ~4 km/pixel | Yagi VHF ✓ |
| Meteor-M N2-3 | LRPT | Visível + IR + vapor d'água | ~1 km/pixel | Yagi VHF ✓ |
| GOES-16 | LRIT | 16 bandas (visível, IR, UV, vapor d'água) | 500m–2 km/pixel | Patch L-band (add-on) |
| GOES-16 | HRIT (full res) | 16 bandas | 500m | Dish 60–90cm (opcional) |

**GOES-16 é o mais valioso para o Brasil:** geoestacionário a 75,2°W, elevação ~55° em Sorocaba, imagens a cada 10 minutos, cobrindo toda a América do Sul. Sinal aberto e gratuito.

**Tipos de análises possíveis:**

| Análise | Bandas | Aplicação |
|---|---|---|
| Cobertura de nuvens | Visível | Previsão do tempo local |
| Temperatura de superfície | IV termal | Monitoramento ambiental, detecção de queimadas |
| Vapor d'água atmosférico | 6,2 / 6,9 / 7,3 μm | Dinâmica atmosférica |
| Índice de vegetação (NDVI) | Visível + NIR | Agronegócio, desmatamento |
| Monitoramento de nuvens convectivas | IV + visível | Detecção de tempestades |
| Poluição atmosférica (AOD) | Múltiplas bandas | Qualidade do ar |

**O que distingue a recepção direta dos dados públicos na internet:** velocidade (dados brutos antes de publicação), resolução máxima (HRIT vs. LRIT), personalização do processamento, e o loop didático de ter alunos recebendo os dados diretamente.

---

### Q: Os sites do GOES, Meteor, NOAA já não disponibilizam as imagens em alta resolução? Ter antenas traz alguma informação exclusiva?

**O que já é público e gratuito:**
- GOES-16: todos os produtos (16 bandas, full disk, mesoscale) disponíveis em tempo real no AWS Open Data e no portal NOAA/CPTEC — sem necessidade de estação própria.
- NOAA APT: imagens de qualidade razoável disponíveis online em sites como weather.uwyo.edu.

**O que é exclusivo de ter uma estação própria:**

| Tipo de dado | Disponível publicamente? | Exclusivo da estação |
|---|---|---|
| Imagens GOES-16/NOAA | Sim, gratuito | Não (mas processamento próprio é educativo) |
| Telemetria de CubeSats | Parcialmente (SatNOGS) | Dados de satélites específicos, horários precisos |
| Dados de sensores IoT próprios | Não | Sim — dados do seu sensor chegam só na sua estação |
| Espectro RF bruto | Não | Sim — monitoramento espectral de qualquer sinal |
| Uplink para satélites | Não | Sim — só quem tem estação pode transmitir |
| Loop didático completo | Não | Sim — aluno vê o dado nascendo da antena |

**Conclusão:** o valor da estação **não está nas imagens meteorológicas** (já públicas), mas no loop didático completo, na capacidade de uplink, nos dados IoT proprietários, e na pesquisa em comunicações de RF.

---

## 5. IoT via Satélite — Sensor de Solo com ESP32 + LoRa

### Q: Para fazer sensores IoT de solo com ESP32 + antena LoRa: qual a potência de transmissão, precisa de homologação da ANATEL, e quais acordos com operadoras de satélite? Existe alguma operadora free para fins acadêmicos?

**Potência de transmissão:**
- Para alcançar um satélite LEO em órbita baixa (~500 km), **< 1W é suficiente** com antena simples apontada para o céu (trifilar ou Yagi).
- LoRa (Spreading Factor SF11–12) compensa a distância com ganho de codificação, não com potência.
- O módulo SX1278/SX1268 dos ESP32 TTGO LoRa32 transmite tipicamente 100–200 mW (20–23 dBm).

**Homologação ANATEL:**
- O módulo ESP32/LoRa precisa ter **Certificado de Homologação ANATEL** (obrigação do fabricante/importador). Módulos comerciais como TTGO LoRa32 vendidos no Brasil normalmente já possuem.
- Para uso experimental em frequências de radioamador (430–440 MHz), o operador precisa de **licença de radioamador** (Certificado de Operador de Estação de Radioamador — COER) emitida pela ANATEL.
- Para uso em frequências ISM (Industrial, Scientific and Medical) — ex: 915 MHz — não há necessidade de licença de operador, desde que dentro dos limites de potência.

**Operadoras de satélite free para fins acadêmicos:**

| Plataforma | Frequência | Protocolo | Custo | Como acessar |
|---|---|---|---|---|
| **FOSSASAT-2E** | 437,525 MHz | LoRa SF11–12, open-source | Gratuito | Registrar no fórum FOSSA Systems |
| **TinyGS** | 433–437 MHz | LoRa (recepção) | Gratuito | tinygs.com |
| **Lacuna Space / TTI** | LoRaWAN satélite | LoRaWAN padrão | Free tier para devs | thethingsindustries.com |
| **SatNOGS / Libre Space** | VHF/UHF diversas | Protocolo aberto | Gratuito (open-source) | satnogs.org |

---

### Q: Onde encontro tutorial para fazer um sensor IoT de solo enviando dados para satélite free?

**Passo a passo recomendado (do simples ao avançado):**

#### Etapa 1 — Sensor de solo com ESP32 (base)
- Tutorial: [ESP32 Soil Moisture Sensor](https://esp32io.com/tutorials/esp32-soil-moisture-sensor)
- Hardware: ESP32 + sensor capacitivo de umidade do solo (HW-390, ~R$ 10)

#### Etapa 2 — Adicionar LoRa ao ESP32
- Tutorial: [ESP32 + LoRa RFM95 no Arduino IDE](https://randomnerdtutorials.com/esp32-lora-rfm95-transceiver-arduino-ide/)
- Tutorial: [ESP32 + LoRa + Sensor + Web Server](https://randomnerdtutorials.com/esp32-lora-sensor-web-server/)
- Hardware: TTGO LoRa32 (ESP32 + SX1278 integrado, ~R$ 80)

#### Etapa 3 — Uplink para satélite via FOSSASAT-2E
- Biblioteca: [RadioLib](https://github.com/jgromes/RadioLib) — instalar via Arduino IDE Library Manager
- Repositório do satélite: [FOSSASystems/FOSSASAT-2](https://github.com/FOSSASystems/FOSSASAT-2)
- Simulação de comunicação bidirecional: [McOrts/fossasat1_satellite-communication-simulation](https://github.com/McOrts/fossasat1_satellite-communication-simulation)
- Registrar no fórum FOSSA Systems para obter acesso à rede
- Parâmetros: 437,525 MHz, LoRa, SF11–12, BW 125 kHz, < 1W

#### Etapa 4 — Receber os dados na estação
- Firmware da estação receptora: [TinyGS](https://github.com/G4lile0/tinyGS)
- Flash via Web Installer: [installer.tinygs.com](https://installer.tinygs.com)
- Dados aparecem no dashboard TinyGS em tempo real

**Loop completo para o projeto PTS:**
```
Sensor ESP32 (IFSP Sorocoba)
  → LoRa uplink 437 MHz (< 1W)
    → FOSSASAT-2E (LEO, ~500 km)
      → Estação TinyGS do PTS (Sorocoba)
        → Dashboard web
```

---

### Q: Para enviar dados para o TinyGS preciso assinar algum serviço?

**Não. TinyGS é 100% gratuito e open-source.**

- Criar conta em [tinygs.com](https://tinygs.com): gratuito
- Operar uma estação receptora: gratuito (hardware ~R$ 80–120)
- Contribuir dados para a rede global: gratuito
- Sustentado por voluntários e doações opcionais

**Porém:** TinyGS é primariamente uma rede **receptora** — suas estações *recebem* pacotes dos satélites. Para *enviar* dados de sensores IoT *para* um satélite, você usa FOSSASAT-2E ou Lacuna Space (não o TinyGS em si). O TinyGS entra como a **estação receptora** que capta os dados depois que o satélite os armazena e retransmite.

---

## 6. Estações Comparáveis no Mundo

### Q: Quais outras estações no mundo têm custo semelhante ao projeto PTS e que tipos de estudos fazem?

| Estação | Localização | Custo aprox. | Equipamento principal | Tipos de estudo |
|---|---|---|---|---|
| **ISISPACE Ground Station** (TU Delft) | Delft, NL | €99–139k | Yagi VHF/UHF + S-band dish 2m + SDR 100/120W | CubeSat TT&C, ADCS, propulsão, comunicações |
| **Morehead State University** | Kentucky, EUA | ~US$ 100–200k | Antenas 21m (grandes!) + VHF/UHF | Referência mundial — downlink de dados científicos, suporte a missões NASA |
| **Libre Space Foundation / SatNOGS** | Distribuída (global) | US$ 300–500/estação | RPi + SDR RTL-SDR + Yagi + rotor | Rede colaborativa global, telemetria open-source |
| **FUNcube / AMSAT** | Várias universidades EU | £20–50k | SDR + Yagi + rotor básico | Educação, downlink de CubeSats |
| **Ground Station típica universitária** | EUA/Europa | US$ 50–150k | SDR USRP B210 + Yagi + SPID rotor | Ensino de engenharia, missões CubeSat próprias |

**Posição do PTS (R$ 187k ≈ US$ 37k / €35k):** compatível com uma estação universitária sólida de nível intermediário, acima de uma estação SatNOGS amadora e abaixo do tier ISISPACE completo. Suficiente para todas as operações educacionais e de pesquisa em CubeSats LEO.

---

## 7. Documentos do Projeto

| Documento | Descrição |
|---|---|
| `NanosatélitesConsultoria.pdf` | Caderno de escopo da Inova Sorocaba (mar/2026): 4 fases, cronograma, sala 56,72m², 30 jovens/ano |
| `formulario FINAL 28032022.pdf` | Formulário FINEP PTSINOVA40 (2022): projeto R$ 14,2M, parceria Alya, 6 componentes, 3 metas físicas |
| `Parecer_Tecnico_EstacaoSolo_SergioShimura.docx` | Parecer técnico emitido em 20/05/2026, endereçado a Mariane, Flávio e André |
| `MiniCurriculo_SergioShimura.docx` | Mini-currículo focado em estação de solo, com pós-doc USP 2024–2025 |
| `Proposta Estação de Solo-Shimura.pptx` | Proposta de consultoria em PowerPoint (10 slides), versão jun/2026 |
| `Parecer Técnico Estação de Solo para Satélites.eml` | Email de Mariane (26/05/2026) com lista de equipamentos aprovados e valores FINEP |

---

## 8. Referências e Fontes

### Regulação

| Fonte | URL |
|---|---|
| ANATEL — Regulamento Geral de Licenciamento | [gov.br/anatel/regulamento-licenciamento](https://www.gov.br/anatel/pt-br/regulado/outorga/regulamento-geral-de-licenciamento) |
| ANATEL — Licenciamento Radioamador (COER) | [gov.br/anatel/radioamador](https://www.gov.br/anatel/pt-br/regulado/outorga/radioamador-e-radio-cidadao/licenciamento-de-estacoes-do-radioamador) |
| ANATEL — Perguntas Frequentes Satélite | [anatel.gov.br/satelite-faq](https://www.anatel.gov.br/setorregulado/perguntas-frequentes?catid=2) |

### Satélites e redes

| Fonte | URL |
|---|---|
| TinyGS — rede global open-source | [tinygs.com](https://tinygs.com) |
| TinyGS — Web Installer (flash sem programação) | [installer.tinygs.com](https://installer.tinygs.com) |
| TinyGS — GitHub | [github.com/G4lile0/tinyGS](https://github.com/G4lile0/tinyGS) |
| FOSSASAT-2 — repositório oficial | [github.com/FOSSASystems/FOSSASAT-2](https://github.com/FOSSASystems/FOSSASAT-2) |
| FOSSASAT — simulação comunicação bidirecional | [github.com/McOrts/fossasat1_satellite-communication-simulation](https://github.com/McOrts/fossasat1_satellite-communication-simulation) |
| Lacuna Space + TTI — free tier satélite LoRaWAN | [thethingsindustries.com/lacuna-space](https://www.thethingsindustries.com/news/lacuna-space-and-the-things-industries-partner-to-provide-free-access-to-direct-to-satellite-lora-connectivity-for-developers-around-the-world/) |
| SatNOGS — Libre Space Foundation | [satnogs.org](https://satnogs.org) |
| GOES-16 — NOAA/NESDIS | [nesdis.noaa.gov/goes-east](https://www.nesdis.noaa.gov/current-satellite-missions/currently-flying/geostationary-satellites/goes-east) |
| GOES-16 — Open Data AWS | [registry.opendata.aws/noaa-goes](https://registry.opendata.aws/noaa-goes/) |
| NOAA APT/HRPT Satellites | [noaa.gov/satellites](https://www.noaa.gov/satellites) |

### Estações de referência

| Fonte | URL |
|---|---|
| ISISPACE Ground Station (TU Delft spin-off) | [isispace.nl/ground-station](https://www.isispace.nl/product/isis-ground-station/) |
| ISISPACE — CubeSatShop (specs + preços) | [cubesatshop.com/isispace](https://www.cubesatshop.com/product/isis-ground-station-system/) |
| Morehead State University Space Science Center | [moreheadstate.edu/csos](https://www.moreheadstate.edu/academics/colleges/science/csos) |
| RTL-SDR — Building a FossaSat LoRa Ground Station | [rtl-sdr.com/fossasat-ground-station](https://www.rtl-sdr.com/building-a-fossasat-1-lora-iot-ground-station/) |

### Tutoriais — ESP32 + LoRa + IoT + Satélite

| Fonte | URL |
|---|---|
| RadioLib — biblioteca universal LoRa/FOSSASAT | [github.com/jgromes/RadioLib](https://github.com/jgromes/RadioLib) |
| Random Nerd Tutorials — ESP32 + LoRa RFM95 | [randomnerdtutorials.com/esp32-lora-rfm95](https://randomnerdtutorials.com/esp32-lora-rfm95-transceiver-arduino-ide/) |
| Random Nerd Tutorials — ESP32 + LoRa + Sensor + Web Server | [randomnerdtutorials.com/esp32-lora-sensor-web-server](https://randomnerdtutorials.com/esp32-lora-sensor-web-server/) |
| ESP32 — Sensor de umidade do solo | [esp32io.com/soil-moisture](https://esp32io.com/tutorials/esp32-soil-moisture-sensor) |
| ESP32 + LoRa + Temperatura + Umidade (GitHub) | [github.com/rch-goldsnaker/esp32-lora-humidity-temperature](https://github.com/rch-goldsnaker/esp32-lora-humidity-temperature) |
| ESP32 + LoRa + Agricultura + RS485 (GitHub) | [github.com/myinvent/ESP32-LoRa-RS485-Agriculture-Kit](https://github.com/myinvent/ESP32-LoRa-RS485-Agriculture-Kit) |
| LoRa Soil Moisture Monitoring — How2Electronics | [how2electronics.com/lora-soil-moisture](https://how2electronics.com/lora-based-soil-moisture-monitoring-on-lora-esp32-webserver/) |

### Artigos científicos

| Fonte | URL |
|---|---|
| IoT Node com LoRa GEO Satélite para Agrofood (MDPI Sensors 2025) | [mdpi.com/1424-8220/25/20/6469](https://www.mdpi.com/1424-8220/25/20/6469) |
| Soil Water Monitoring com LoRa (MDPI Sensors 2024) | [mdpi.com/1424-8220/24/24/8104](https://www.mdpi.com/1424-8220/24/24/8104) |
| Low-Cost IoT Smart Agricultural System com ESP32 + LoRa (IEEE 2025) | [ieeexplore.ieee.org/10928022](https://ieeexplore.ieee.org/document/10928022/) |

---

*Documento atualizado em 09/06/2026 — Sessão de consultoria técnica.*
