
# PBL_Project_Based_Learning

Este repositório documenta o projeto final colaborativo **"PBL - Project-Based Learning"**, desenvolvido no contexto das disciplinas **Comunicação de Dados e Redes II** e **Segurança de Redes e Sistemas**. O objetivo do projeto foi o planeamento, configuração e implementação de uma topologia de rede para um campus universitário, com a devida aplicação de medidas de segurança, realizado no curso de Informática (2.º ano) da UMAIA.

Aqui serão registados todos os passos do desenvolvimento do projeto, desde o enunciado e explicações iniciais até à definição da rede, configurações técnicas implementadas e as soluções de segurança adotadas. O repositório tem como objetivo proporcionar uma visão detalhada do processo, com foco na construção de uma infraestrutura de rede segura, eficiente e alinhada aos requisitos técnicos especificados no PDF fornecido.

---

# Enunciado do Projeto 

[PBL_Enunciado](./PBL_Enunciado) 

---

# Desenvolvimento

## 1. Topologia física e lógica 

<details>
  <summary><strong>1.1.1 DATACENTER</strong></summary>

  ### Serviços Internos

   - **Servidor DHCP para todas as redes**
   - **Servidor do website institucional (HTTP)**
   - **Servidor FTP para Departamento de Serviços de Informática**
   - **Servidor HTTP para Professores e Departamento de Serviços Académicos**
  
  ### WAN

  - **Internet**

</details>


<details>
  <summary><strong>1.1.2 EDIFÍCIO A</strong></summary>

  ### BASTIDOR 1

  **Geral do edifício**
   - 8 Impressoras
   - 4 Telefones
   - 1 PC para convidados

  **Sala do Departamento de Serviços de Informática**
   - 5 PCs (serviços de informática)
   - 5 Telefones

  **Sala A1**
   - 2 PCs para professor
   - 2 Telefones
   - 50 PCs para alunos

  ### BASTIDOR 2

  **Sala A2**
   - 2 PCs para professor
   - 2 Telefones
   - 15 PCs para alunos

  **Sala A3**
   - 2 PCs para professor
   - 2 Telefones
   - 15 PCs para alunos
</details>

<details>
  <summary><strong>1.1.3 EDIFÍCIO B</strong></summary>

  ### BASTIDOR 1

  **Laboratório de Informática**
   - 120 PCs para alunos
   - 2 PCs para professores
   - 1 Telefone

  **Auditório**
   - 2 PCs para professor
   - 1 Telefone

  ### BASTIDOR 2

  **Geral do edifício**
   - 7 Impressoras
   - 4 Telefones
   - 1 PC para convidados

  **Sala do Departamento de Serviços Financeiros**
   - 10 PCs (serviços financeiros)
   - 5 Telefones

  **Sala do Departamento de Serviços Académicos**
   - 16 PCs (serviços académicos)
   - 10 Telefones

  **Sala de Professores**
   - 25 PCs para professores
   - 4 PCs para convidados
   - 3 Telefones

  **Laboratório de Informática**
   - 120 PCs para alunos
   - 2 PCs para professores
   - 1 Telefone

  **Sala de Aulas B1**
   - 2 PCs para professor
   - 1 Telefone
   - 35 PCs para alunos
</details>


# 2. Endereçamento IPv4 

## SWITCHES

<details>
  <summary><strong>SWITCHES – EDIFÍCIO A</strong></summary>

  | **Batidor** | **Switch** | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
  |-------------|------------|----------|---------------------|---------------------|---------------------|
  | 1           | BA1-S1     | 90       | 192.168.90.11       | 255.255.255.224     | 192.168.90.1       |
  | 1           | BA1-S2     | 90       | 192.168.90.12       | 255.255.255.224     | 192.168.90.1       |
  | 1           | BA1-S3     | 90       | 192.168.90.13       | 255.255.255.224     | 192.168.90.1       |
  | 1           | BA1-S4     | 90       | 192.168.90.14       | 255.255.255.224     | 192.168.90.1       |
  | 2           | BA2-S5     | 90       | 192.168.90.21       | 255.255.255.224     | 192.168.90.1       |
  | 2           | BA2-S6     | 90       | 192.168.90.22       | 255.255.255.224     | 192.168.90.1       |
</details>

<details>
  <summary><strong>SWITCHES – EDIFÍCIO B</strong></summary>

  | **Batidor** | **Switch** | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
  |-------------|------------|----------|---------------------|---------------------|---------------------|
  | 1           | BB1-S1     | 91       | 192.168.91.11       | 255.255.255.224     | 192.168.91.1       |
  | 1           | BB1-S2     | 91       | 192.168.91.12       | 255.255.255.224     | 192.168.91.1       |
  | 1           | BB1-S3     | 91       | 192.168.91.13       | 255.255.255.224     | 192.168.91.1       |
  | 1           | BB1-S4     | 91       | 192.168.91.14       | 255.255.255.224     | 192.168.91.1       |
  | 1           | BB1-S5     | 91       | 192.168.91.15       | 255.255.255.224     | 192.168.91.1       |
  | 1           | BB1-S6     | 91       | 192.168.91.16       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S1     | 91       | 192.168.91.21       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S2     | 91       | 192.168.91.22       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S3     | 91       | 192.168.91.23       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S4     | 91       | 192.168.91.24       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S5     | 91       | 192.168.91.25       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S6     | 91       | 192.168.91.26       | 255.255.255.224     | 192.168.91.1       |
  | 2           | BB2-S7     | 91       | 192.168.91.27       | 255.255.255.224     | 192.168.91.1       |
</details>

<details>
  <summary><strong>SWITCHES – DATACENTER</strong></summary>

  | **Switch**           | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
  |----------------------|----------|---------------------|---------------------|---------------------|
  | LAN-DATACENTER       | 92       | 192.168.92.2        | 255.255.255.224     | 192.168.92.1       |
</details>

## ROUTERS

<details>
  <summary><strong>ROUTERS</strong></summary>

  | **Router**          | **Interface** | **Endereço IP** |
  |---------------------|---------------|-----------------|
  | **ROUTER CENTRAL**  | e0/0          | 10.0.1.2        |
  |                     | e0/1          | 10.0.2.2        |
  |                     | e0/2          | 10.0.3.2        |
  |                     | e0/3          | 10.0.4.2        |
  | **ROUTER A**        | e0/1          | 10.0.1.1        |
  | **ROUTER B**        | e0/0          | 10.0.2.1        |
  | **ROUTER DATABASE** | e0/0          | 10.0.3.1        |
  |                     | e0/1.92       | 192.168.92.1    |
  |                     | e0/1.93       | 192.168.93.1    |
  | **ROUTER ISP**      | e0/0          | 10.0.4.1        |
  |                     | e0/1          | 192.168.94.1    |
</details>

## VLANs

<details>
  <summary><strong>VLANs</strong></summary>

  | **VLAN ID** | **Nome VLAN**            | **Segmento**         | **Local**       | **Nº Hosts** | **Nº Hosts Reais** | **CIDR** | **Sub-rede**         | **Gateway**        | **Máscara**         | **IPs utilizáveis** |
  |-------------|--------------------------|----------------------|-----------------|--------------|--------------------|----------|----------------------|--------------------|---------------------|---------------------|
  | 10          | VLAN_ALUNOS_A            | Alunos               | Edifício A      | 80           | 83                 | /25      | 192.168.10.0/25      | 192.168.10.1      | 255.255.255.128     | .2 – .126           |
  | 11          | VLAN_ALUNOS_B            | Alunos               | Edifício B      | 155          | 158                | /24      | 192.168.11.0/24      | 192.168.11.1      | 255.255.255.0       | .2 – .254           |
  | 20          | VLAN_PROFESSORES_A       | Professores          | Edifício A      | 6            | 9                  | /28      | 192.168.20.0/28      | 192.168.20.1      | 255.255.255.240     | .2 – .14            |
  | 21          | VLAN_PROFESSORES_B       | Professores          | Edifício B      | 31           | 34                 | /26      | 192.168.21.0/26      | 192.168.21.1      | 255.255.255.192     | .2 – .62            |
  | 30          | VLAN_SERV_FINANCEIROS    | Serviços Financeiros | Edifício B      | 10           | 13                 | /28      | 192.168.30.0/28      | 192.168.30.1      | 255.255.255.240     | .2 – .14            |
  | 40          | VLAN_SERV_ACADEMICOS     | Serviços Académicos  | Edifício B      | 16           | 19                 | /27      | 192.168.40.0/27      | 192.168.40.1      | 255.255.255.224     | .2 – .30            |
  | 50          | VLAN_SINFO               | Serviços Informática | Edifício A      | 5            | 8                  | /28      | 192.168.50.0/28      | 192.168.50.1      | 255.255.255.240     | .2 – .14            |
  | 60          | VLAN_CONVIDADOS_A        | Convidados           | Edifício A      | 1            | 4                  | /29      | 192.168.60.0/29      | 192.168.60.1      | 255.255.255.248     | .2 – .6             |
  | 61          | VLAN_CONVIDADOS_B        | Convidados           | Edifício B      | 5            | 8                  | /28      | 192.168.61.0/28      | 192.168.61.1      | 255.255.255.240     | .2 – .14            |
  | 70          | VLAN_TELEFONES_A         | Telefones            | Edifício A      | 15           | 18                 | /27      | 192.168.70.0/27      | 192.168.70.1      | 255.255.255.224     | .2 – .30            |
  | 71          | VLAN_TELEFONES_B         | Telefones            | Edifício B      | 25           | 28                 | /27      | 192.168.71.0/27      | 192.168.71.1      | 255.255.255.224     | .2 – .30            |
  | 80          | VLAN_IMPRESSORAS_A       | Impressoras          | Edifício A      | 8            | 11                 | /28      | 192.168.80.0/28      | 192.168.80.1      | 255.255.255.240     | .2 – .14            |
  | 81          | VLAN_IMPRESSORAS_B       | Impressoras          | Edifício B      | 7            | 10                 | /28      | 192.168.81.0/28      | 192.168.81.1      | 255.255.255.240     | .2 – .14            |
  | 90          | VLAN_GESTAO_REDE_A       | Gestão equipamentos  | Edifício A      | 5            | 8                  | /27      | 192.168.90.0/27      | 192.168.90.1      | 255.255.255.224     | .2 – .30            |
  | 91          | VLAN_GESTAO_REDE_B       | Gestão equipamentos  | Edifício B      | 5            | 8                  | /27      | 192.168.91.0/27      | 192.168.91.1      | 255.255.255.224     | .2 – .30            |
  | 92          | VLAN_GESTAO_REDE_DATASET | Gestão equipamentos  | Datacenter      | 5            | 8                  | /27      | 192.168.92.0/27      | 192.168.92.1      | 255.255.255.224     | .2 – .30            |
  | 93          | DATACENTER               | Datacenter           | Datacenter      | 29           | 29                 | /27      | 192.168.93.0/27      | 192.168.93.1      | 255.255.255.224     | .2 – .30            |
  | 94          | ISP                      | ISP                  | Datacenter      | 29           | 29                 | /29      | 192.168.94.0/29      | 192.168.94.1      | 255.255.255.248     | .2 – .6             |
</details>






