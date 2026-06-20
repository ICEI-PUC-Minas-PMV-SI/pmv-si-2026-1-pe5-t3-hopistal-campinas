# Hospital Campinas Saúde — Projeto de Infraestrutura de Redes

`CURSO: Sistemas de Informação`

`DISCIPLINA: Projeto - Projeto de Infraestrutura de Redes`

`Eixo: 5`

O **Hospital Campinas Saúde** é um projeto de infraestrutura de redes que simula o ambiente de TI de uma rede hospitalar composta por três unidades: a **Matriz**, a **UPA Ouro Verde** e a **UPA Campo Grande**. O projeto contempla todo o ciclo de uma infraestrutura corporativa — desde o planejamento e endereçamento IP, passando pela implantação de serviços de rede (DHCP, DNS, compartilhamento de arquivos), pela hospedagem de serviços em nuvem (AWS), pela gerência e monitoração dos servidores, até a análise e os mecanismos de Segurança da Informação.

A solução adota um modelo híbrido (*on-premise* + nuvem): serviços críticos de rede residem na infraestrutura local da Matriz (virtualizada em Oracle VirtualBox), enquanto o sistema de prontuários eletrônicos, o banco de dados e a aplicação back-end ficam centralizados na Amazon Web Services (AWS), acessíveis de forma segura por todas as unidades.

## Integrantes

* Italo Rangel Penaforte Mendes
* Rodrigo Figueira de Lima
* João de Sousa Lourenço
* Ryann Victor de Almeida Parreira
* Luigi Rodrigo dos Santos de Moura
* Rodrigo Carvalho Cattoi da Costa

## Orientador

* Alexandre Teixeira

## Etapas do Projeto

| Etapa | Tema | Descrição |
|-------|------|-----------|
| **1** | Planejamento e Endereçamento | Projeto de endereçamento IP das três unidades e simulação da topologia no Cisco Packet Tracer. |
| **2** | Implantação de Ambientes | Virtualização local (Oracle VirtualBox) com DHCP, DNS (BIND9) e servidor de arquivos (Samba); ambiente em nuvem AWS com instância EC2 (Apache + PHP) e banco de dados MySQL. |
| **3** | Gerência e Monitoração | Monitoramento dos servidores com **Zabbix 7.4.10**, utilizando Zabbix Agent 2 e SNMP sobre instâncias EC2 (Ubuntu 24.04 LTS). |
| **4** | Mecanismos de Segurança | Aplicação back-end (Ruby on Rails) implantada em Amazon ECS, análise de vulnerabilidades baseada no **OWASP Top 10 (2025)**, Política de Segurança da Informação e Cartilha de Boas Práticas. |

## Arquitetura de Rede

| Unidade | Rede | Gateway | Faixa DHCP |
|---------|------|---------|------------|
| Hospital Matriz (Core) | 192.168.0.0/24 | 192.168.0.1 | 192.168.0.50 – 192.168.0.200 |
| UPA Ouro Verde | 192.168.1.0/24 | 192.168.1.1 | 192.168.1.50 – 192.168.1.200 |
| UPA Campo Grande | 192.168.2.0/24 | 192.168.2.1 | 192.168.2.50 – 192.168.2.200 |

### Principais tecnologias

* **Virtualização local:** Oracle VirtualBox (Ubuntu Server 22.04 LTS)
* **Serviços de rede:** isc-dhcp-server, BIND9 (domínio `hospital.local`), Samba
* **Nuvem:** Amazon Web Services — EC2 (t2.micro), Amazon ECS
* **Aplicação web:** Apache + PHP; back-end em Ruby on Rails 8.1.3 (Ruby 4.0.5)
* **Banco de dados:** MySQL 8.0 / SQLite 3
* **Monitoramento:** Zabbix (Agent 2 e SNMP)
* **Simulação de topologia:** Cisco Packet Tracer

## Documentação

A documentação completa de cada etapa está disponível na pasta [`docs/`](docs/):

* [`projeto-infraestrutura-redes.pdf`](docs/projeto-infraestrutura-redes.pdf) — Etapas 1 e 2 (planejamento e implantação dos ambientes)
* [`monitoramento-zabbix.pdf`](docs/monitoramento-zabbix.pdf) — Etapa 3 (gerência e monitoração com Zabbix)
* [`backend.pdf`](docs/backend.pdf) — Etapa 4 (back-end e análise de vulnerabilidades OWASP)
* [`politica-seguranca-informacao.pdf`](docs/politica-seguranca-informacao.pdf) — Política de Segurança da Informação (PSI)
* [`cartilha-boas-praticas.pdf`](docs/cartilha-boas-praticas.pdf) — Cartilha de Boas Práticas de Acesso Seguro
* [`projeto-redes.zip`](docs/projeto-redes.zip) — Arquivos de simulação do Cisco Packet Tracer
