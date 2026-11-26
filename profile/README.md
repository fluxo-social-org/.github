<div align="center">
  <img src="./assets/banner.svg" alt="Fluxo Social — Sistema de Gestão Operacional CRAS / SUAS" width="100%" />

  <br /><br />

  <p>
    <img src="https://img.shields.io/badge/Java-21_LTS-004ECC?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21 LTS" />
    <img src="https://img.shields.io/badge/Spring_Boot-3.4-0F6355?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 3.4" />
    <img src="https://img.shields.io/badge/React-19_%2B_Vite_8-004ECC?style=for-the-badge&logo=react&logoColor=white" alt="React 19 + Vite 8" />
    <img src="https://img.shields.io/badge/PostgreSQL-16_%2B_Flyway-0F6355?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL 16 + Flyway" />
    <img src="https://img.shields.io/badge/Observabilidade-Prometheus_%2B_Grafana_%2B_Loki-1A1C22?style=for-the-badge&logo=grafana&logoColor=F46800" alt="Prometheus + Grafana + Loki" />
    <img src="https://img.shields.io/badge/Acessibilidade-e--MAG_%2F_WCAG_2.1_AAA-FFB800?style=for-the-badge&labelColor=1A1B1F" alt="e-MAG / WCAG 2.1 AAA" />
  </p>
</div>

---

### 📖 Nossa História: do TCC na UniALFA à Plataforma GovTech

O **Fluxo Social** nasceu em 2026 como Trabalho de Conclusão de Curso (TCC) em **Tecnologia em Sistemas para Internet** na **Faculdade ALFA Umuarama (UniALFA)**, desenvolvido a partir de entrevistas reais em campo com recepcionistas, técnicos e coordenadores dos CRAS da **Secretaria Municipal de Assistência Social (SMAS) de Umuarama - PR**.

Na visita técnica, encontramos uma dor comum à assistência social pública brasileira: mais de **5.000 fichas físicas em papel** espalhadas por gavetas e planilhas desconectadas, gerando lentidão em atendimentos de urgência, risco de extravio de dados sigilosos, duplicidade de cadastros entre unidades e retrabalho na geração de relatórios do SUAS.

Após a **aprovação pela banca examinadora** (marco histórico congelado na tag `v0.9.0-tcc`), criamos esta organização para governar o projeto de forma colaborativa e conduzir o **Plano Diretor Pós-TCC**: endurecer a arquitetura para entrega gratuita em produção *On-Premise* nos CRAS de Umuarama (`v1.0.0 — Edição CRAS`) e evoluir a base para uma plataforma SUAS completa (`v2.0.0+`).

---

### 🧩 O que o Sistema Entrega

Estruturado como **Monolito Modular** com isolamento lógico por unidade (`cras_id`) e entrega *offline-ready* via Docker + Nginx:

* **Recepção, Triagem e Cadastros Base:** busca global unificada por CPF/NIS (prevenindo duplicidade entre os 3 CRAS e 320 bairros oficiais), nome social, composição familiar e endereço automático via ViaCEP.
* **Agendamentos, Jornadas e Salas:** escalas configuráveis por unidade e técnico de referência, controle de ocupação de salas físicas e encaixes emergenciais com justificativa obrigatória.
* **Prontuário Eletrônico & Sigilo SUAS:** evoluções técnicas com *auto-save* local contra oscilações de rede, Plano de Acompanhamento Familiar (PAF), anexos validados via Apache Tika e sigilo psicossocial compartimentado (CFESS/CRESS e CFP).
* **Benefícios Eventuais & Calamidade Pública:** catálogo de critérios, controle de cotas/orçamento mensal, homologação pela coordenação e aportes de contingência em decretos de emergência.
* **Relatórios Oficiais & Validação Pública:** Painel CRAS e **RMA Oficial (MDS — Blocos I, II e III)** com exportação em **PDF, XLSX e CSV**, além de portal público `/validar-documento` para conferir declarações e guias emitidas (`FS-UMU-...`).
* **Segurança, LGPD e Engenharia de Produção:** mascaramento de CPF/NIS no servidor com revelação auditada, RBAC granular com overrides por servidor, bloqueio por inatividade, CI bloqueante (**Gitleaks + Trivy**), observabilidade completa (**Actuator, OpenTelemetry, Prometheus, Loki, Grafana Alloy e Web Vitals**) e suíte nativa de testes de carga (**Grafana k6** simulando 20 mil famílias / 65 mil cidadãos em hardware municipal de 2 vCPU / 4 GB RAM).

---

### 🚀 Linha do Tempo e Roadmap

| Marco | Escopo | Status |
| :--- | :--- | :---: |
| **Programa GovTech (Fases 0–7)** | Fundação 12-Factor, RBAC no PostgreSQL, bloqueio de sessão, LGPD/sigilo, acessibilidade e-MAG, territorialização/RMA, Flyway/Nginx e transferências territoriais | **Concluído ✅** |
| **TCC Aprovado (`v0.9.0-tcc`)** | Entrega completa defendida na UniALFA com 15 ADRs, OpenAPI 3.0 e ambiente Docker de produção | **Congelado ✅** |
| **Onda P0 (`P0.A`–`P0.G`)** | Higiene, hardening Nginx `:80`, `parametros_suas`, observabilidade ponta a ponta, benchmark k6, reconstrução da matriz RBAC (`P0.A`–`P0.F` ✅) e papel `SUPER_ADMIN` DTI (`P0.G` 📋) | **Em andamento 🔄** |
| **Onda P1 (`v1.0.0` Edição CRAS)** | Escala SQL (`GROUP BY`), simplificação de UX (Prontuário, Triagem Rápida, Central de Relatórios + `Ctrl+K` + VLibras), PostgreSQL 18 + Boot 4.1 + Java 25 LTS e E2E Playwright | **Planejado 📋** |
| **Onda P2 (`v2.0.0+` Plataforma SUAS)** | Modo Dual (`onprem` \| `saas` multi-município), CREAS/PAEFI, Centro POP, SCFV, CadÚnico e Gov.BR | **Visão Futura 🔭** |

---

### 🎨 Design System Governamental

Convergência entre **Bold (Bridge/UFSC)**, **DS Gov.BR / e-MAG** e **Material Design 3**, priorizando **Modo Claro ergonômico** para monitores de atendimento público, **Modo Escuro com acento Esmeralda** e **Alto Contraste (WCAG 2.1 AAA)**.

| Token Semântico | Light Mode (Padrão) | Dark Mode | Uso Principal |
| :--- | :---: | :---: | :--- |
| **Primária · Azul Real Umuarama** | `#004ECC` / `#0066FF` | `#60A5FA` | Ações principais, botões e links |
| **Secundária · Amarelo Ouro** | `#FFB800` *(texto `#1A1B1F` obrigatório)* | `#FBBF24` | Alertas, badges e destaques institucionais |
| **Terciária · Verde Menta / Esmeralda** | `#0F6355` | `#5CDDAA` | Apoio social, prontuário e PAIF |
| **Superfícies & Tipografia** | `#FFFFFF` / `#F4F4F8` · Manrope + Inter | `#111215` / `#1A1C22` | Cards, painéis e tabelas de alta densidade |

---

### 📚 Repositório e Documentação Canônica

* 🏛️ **[`fluxo-social-org/fluxo-social`](https://github.com/fluxo-social-org/fluxo-social)** — Monorepo oficial (Backend Java/Spring Boot, Frontend React/Vite, Observabilidade e Stress Tests k6)
* 🗺️ **[Índice Geral da Documentação (`docs/`)](https://github.com/fluxo-social-org/fluxo-social/blob/main/docs/README.md)**
* 🚀 **[Programa de Modernização GovTech (Fases 0–7)](https://github.com/fluxo-social-org/fluxo-social/blob/main/docs/modernizacao-govtech/README.md)**
* 📈 **[Plano Diretor Pós-TCC (`v1.0.0` e `v2.0.0+`)](https://github.com/fluxo-social-org/fluxo-social/blob/main/docs/evolucao-pos-tcc/README.md)**
* 🧱 **[Registros de Decisão Arquitetural (ADRs 001–015)](https://github.com/fluxo-social-org/fluxo-social/tree/main/docs/adrs)**
* 🎨 **[Design System & Acessibilidade e-MAG](https://github.com/fluxo-social-org/fluxo-social/blob/main/docs/design-system/design-system.md)**
* ⚡ **[Suíte de Stress Test & Benchmark (`perf/`)](https://github.com/fluxo-social-org/fluxo-social/blob/main/perf/README.md)**

---

### 👥 Equipe Fundadora

| Integrante | GitHub | Foco & Contribuições |
| :--- | :--- | :--- |
| **Daniel Satel Pereira** | [@Peridan1](https://github.com/Peridan1) | Arquitetura, governança GovTech, segurança/LGPD, observabilidade, benchmark k6 e plano diretor pós-TCC |
| **Felipe Pestana** | [@Pestanadev](https://github.com/Pestanadev) | Coautor do Fluxo Social · *<!-- Felipe: fique à vontade para adicionar seus destaques e links aqui -->* |
| **Keltton Felipe Alves Silveira** | [@Keltton](https://github.com/Keltton) | Coautor do Fluxo Social · Integração de API e módulos operacionais · *<!-- Keltton: fique à vontade para adicionar seus destaques e links aqui -->* |

---

<div align="center">
  <sub>Desenvolvido com propósito público em Umuarama - PR · Licença MIT</sub>
</div>
