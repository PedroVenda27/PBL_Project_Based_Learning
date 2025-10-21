# PBL_Project_Based_Learning

# PBL_Project_Based_Learning

Este repositório documenta o projeto final colaborativo **"PBL - Project-Based Learning"**, desenvolvido no contexto das disciplinas **Comunicação de Dados e Redes II** e **Segurança de Redes e Sistemas**. O objetivo do projeto foi o planeamento, configuração e implementação de uma topologia de rede para um campus universitário, com a devida aplicação de medidas de segurança, realizado no curso de Informática (2.º ano) da UMAIA.

Aqui serão registados todos os passos do desenvolvimento do projeto, desde o enunciado e explicações iniciais até à definição da rede, configurações técnicas implementadas e as soluções de segurança adotadas. O repositório tem como objetivo proporcionar uma visão detalhada do processo, com foco na construção de uma infraestrutura de rede segura, eficiente e alinhada aos requisitos técnicos especificados no PDF fornecido.


# Enunciado do Projeto 



## 1. Introduction
- Trabalho laboratorial comum às disciplinas de:
    - Comunicação de Dados e Redes II
    - Segurança de Redes e Sistemas
- Trabalho a realizar em grupos de até três elementos, em ambiente GNS3.
- Data de apresentação:
    - Turma A: 17/06/2024
    - Turma B: 23/06/2024
- Entregáveis: Apresentação + projeto GNS3.

## 2. Contextualização
A Figura 1 representa as várias áreas tecnológicas existentes no campus da Universidade da Maia.

<img width="825" height="567" alt="image" src="https://github.com/user-attachments/assets/ca43599c-cf4a-4eb5-803c-75c76feba472" />


Do ponto de vista dos utilizadores da Universidade, é possível identificar 9 segmentos:
1. Alunos
2. Professores
3. Departamento de Serviços Financeiros
4. Departamento de Serviços Académicos
5. Departamento de Serviços de Informática
6. Convidados
7. Telefones
8. Impressoras
9. Gestão dos equipamentos de rede

Como principal objetivo deste trabalho, propõe-se o desenho e implementação de uma arquitetura de rede e serviços de acordo com os requisitos apresentados neste documento.

## 3. Requisitos

### 3.1 Datacenter
O Datacenter é composto por dois âmbitos distintos: a sua rede local, que hospeda os serviços internos da Universidade, e a WAN que suporta a conectividade com o fornecedor de serviços responsável pela interligação à Internet. 

Os servidores deverão estar todos na mesma rede e o seu endereçamento deverá ser atribuído manualmente. O switch de Datacenter, os routers (Datacenter, Central e ISP) e os servidores deverão estar alojados no Bastidor de Datacenter (BD1).

#### 3.1.1 Necessidades de Layer 2 e Layer 3
- **Serviços Internos**
    - Servidor DHCP para todas as redes
    - Servidor do website institucional (HTTP)
    - Servidor FTP para Departamento de Serviços de Informática
    - Servidor HTTP para Professores e Departamento de Serviços Académicos
- **WAN**
    - Internet

### 3.2 Edifício A
O Edifício A da Universidade é composto por 3 salas de aula e a sala do Departamento de Serviços de Informática. Este edifício dispõe de duas zonas técnicas com bastidores.

Um dos bastidores (BA1) aloja os switches necessários para a ligação dos equipamentos terminais gerais do edifício, da sala de aulas A1 e do Departamento de Serviços de Informática. O router do Edifício A deve estar instalado neste bastidor.

O outro bastidor (BA2), deverá alojar os switches responsáveis pelas ligações de rede das salas de aulas A2 e A3.

#### 3.2.1 Necessidades de Layer 2 e Layer 3
- **Geral do edifício**
    - 8 Impressoras
    - 4 Telefones
    - 1 PC para convidados
- **Sala do Departamento de Serviços de Informática**
    - 5 PCs (serviços de informática)
    - 5 Telefones
- **Salas de Aula**
    - **Sala A1**
        - 2 PC para professor
        - 2 Telefone
        - 50 PCs para alunos
    - **Sala A2**
        - 2 PC para professor
        - 2 Telefone
        - 15 PCs para alunos
    - **Sala A3**
        - 2 PC para professor
        - 2 Telefone
        - 15 PCs para alunos

### 3.3 Edifício B
O Edifício B da Universidade é composto por 1 auditório, 2 salas de departamentos, 1 sala de professores, um laboratório de informática e uma sala de aulas. Este edifício dispõe de duas zonas técnicas onde se encontram instalados os bastidores.

Um dos bastidores (BB1) deverá alojar os equipamentos do laboratório de informática e do auditório.

O outro bastidor (BB2) é responsável pela ligação dos equipamentos terminais dos restantes espaços.

#### 3.3.1 Necessidades de Layer 2 e Layer 3
- **Geral do edifício**
    - 7 Impressoras
    - 4 Telefones
    - 1 PC para convidados
- **Auditório**
    - 2 PC para professor
    - 1 Telefone
- **Sala do Departamento de Serviços Financeiros**
    - 10 PCs (serviços financeiros)
    - 5 Telefones
- **Sala do Departamento de Serviços Académicos**
    - 16 PCs (serviços académicos)
    - 10 Telefones
- **Sala de Professores**
    - 25 PCs para professores
    - 4 PC para convidados
    - 3 Telefones
- **Laboratório de Informática**
    - 120 PCs para alunos
    - 2 PCs para professores
    - 1 Telefone
- **Sala de Aulas B1**
    - 2 PCs para professor
    - 1 Telefone
    - 35 PCs para alunos

### 3.4 Endereçamento IP e Conetividade
Cada edifício deverá contemplar uma rede IPv4 por cada um dos segmentos. O endereçamento IPv4 deverá ser criado de acordo com o número de equipamentos necessários por cada um dos segmentos, promovendo-se a utilização de máscaras de rede adaptadas às necessidades.

Relativamente aos requisitos de conectividade, considera-se que deverá existir conectividade IP entre todos os segmentos da topologia.

### 3.5 Controlo de acessos
Relativamente aos requisitos de controlo de acessos entre cada um dos segmentos, considera-se que as seguintes políticas deverão ser implementadas:

- **Alunos**
    - Acesso inter-edifícios
    - Acesso à Internet
    - Acesso a serviços internos (dhcp e website institucional)
    - Acesso a impressoras do edifício
- **Professores**
    - Acesso inter-edifícios
    - Acesso à Internet
    - Serviços internos (dhcp, website institucional e servidor web)
    - Acesso a impressoras do edifício
- **Departamento de Serviços Financeiros**
    - Acesso à Internet
    - Serviços internos (dhcp, website institucional)
    - Acesso a impressoras do edifício
- **Departamento de Serviços Académicos**
    - Acesso à Internet
    - Serviços internos (dhcp, website institucional e servidor web)
    - Acesso a impressoras do edifício
- **Departamento de Serviços de Informática**
    - Acesso a todas as redes
    - Acesso à Internet
    - Acesso a todos os serviços internos
    - Acesso a impressoras do edifício
- **Convidados**
    - Apenas acesso à Internet
- **Telefones**
    - Acesso inter-edifício
    - Serviços internos (dhcp)
- **Impressoras**
    - Serviços internos (dhcp)
- **Gestão dos equipamentos de rede**
    - Acesso inter-edifício
    - Serviços internos (dhcp)

Deverá ser possível aceder ao website institucional a partir da Internet. Todos os fluxos de tráfego não identificados não deverão ser permitidos.

## 4. Objetivos de implementação

### Implementação Essencial (IE)
- Topologia física e lógica
- Endereçamento IPv4
- VLANs + Convidados = Native VLAN
- Routing estático
- Router on-a-stick (Edifício A)
- Legacy Inter-VLAN Routing (Edifício B)
- Servidor DHCP (Router Datacenter)
- Redundância de L2 (STP)
- Rede dedicada à gestão dos equipamentos
- Políticas de controlo de acesso
- Segurança VLANs
- Servidor HTTP e FTP
- Implementação de Port Security
- Segurança STP

### Implementação Avançada (IA)
- LACP
- Redundância de L3 (routing edifícios <-> DC)
- NAT/PAT
- Private VLAN

## 5. Avaliação

### 5.1 Checkpoints
**Turma A:**
- Semana 26/05 a 30/05: Planeamento (VLANs, Endereçamento IPv4, Topologia física e lógica)
- Semana 02/06 a 06/06: Implementação Essencial (IE)
- Semana 09/06 a 13/06: Implementação Avançada (IA)
- Semana 16/06 a 20/06: Apresentação e entrega do trabalho

**Turma B:**
- Semana 26/05 a 30/05: Planeamento (VLANs, Endereçamento IPv4, Topologia física e lógica)
- Semana 02/06 a 06/06: Planeamento + Implementação Essencial (IE)
- Semana 09/06 a 13/06: IE + Implementação Avançada (IA)
- Semana 16/06 a 20/06: IA
- Dia 23/06: Apresentação e entrega do trabalho

### 5.2 Critérios
- Implementação*50% + Checkpoints*20% + Defesa*30%
- Implementação = IE <= 16 | IA <=20
- Checkpoints: Evolução da implementação
- Defesa: Apresentação (20 min.) + Arguição (20 min.)
You can use this markdown for a clear and organized format of your project document!

Is this conversation helpful so far?




Foi detetada atividade suspeita
Parece que outra pessoa pode estar a usar a sua conta do ChatGPT. Garanta a segurança da sua conta para voltar a ter acesso a todas as funcionalidades. Saber mais.



Nenhum ficheiro selecionadoNenhum ficheiro selecionado
O ChatGPT pode cometer erros. Considere verificar informações importantes. Consulte as Preferências de cookies.
