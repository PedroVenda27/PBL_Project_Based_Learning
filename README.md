
# PBL_Project_Based_Learning

Este repositório documenta o projeto final colaborativo **"PBL - Project-Based Learning"**, desenvolvido no contexto das disciplinas **Comunicação de Dados e Redes II** e **Segurança de Redes e Sistemas**. O objetivo do projeto foi o planeamento, configuração e implementação de uma topologia de rede para um campus universitário, com a devida aplicação de medidas de segurança, realizado no curso de Informática (2.º ano) da UMAIA.

Aqui serão registados todos os passos do desenvolvimento do projeto, desde o enunciado e explicações iniciais até à definição da rede, configurações técnicas implementadas e as soluções de segurança adotadas. O repositório tem como objetivo proporcionar uma visão detalhada do processo, com foco na construção de uma infraestrutura de rede segura, eficiente e alinhada aos requisitos técnicos especificados no PDF fornecido.

---

# Enunciado do Projeto 

[PBL_Enunciado](./PBL_Enunciado) 

---

# Desenvolvimento

# 1. Topologia física e lógica 

| ![Edificio B](https://github.com/user-attachments/assets/9a0cce6f-b852-43b1-9b73-7e9f6861d124) | ![DATACENTER](https://github.com/user-attachments/assets/23fbd50c-b51b-4ac2-a789-a190bcfc5ece) | ![Edificio A](https://github.com/user-attachments/assets/dc9b04bb-0f99-4ad3-9167-401552a78f31) |
|---|---|---|

<details open>
  <summary><strong>1.1.1 DATACENTER</strong></summary>

  ### Serviços Internos

   - **Servidor DHCP para todas as redes**
   - **Servidor do website institucional (HTTP)**
   - **Servidor FTP para Departamento de Serviços de Informática**
   - **Servidor HTTP para Professores e Departamento de Serviços Académicos**
  
  ### WAN

  - **Internet**

</details>

<details open>
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


<details open>
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

<details open>
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

<details open>
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

<details open>
  <summary><strong>SWITCHES – DATACENTER</strong></summary>

  | **Switch**           | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
  |----------------------|----------|---------------------|---------------------|---------------------|
  | LAN-DATACENTER       | 92       | 192.168.92.2        | 255.255.255.224     | 192.168.92.1       |
</details>

## ROUTERS

<details open>
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

<details open>
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




# 3. VLANs

## 3.1 CRIAR VLANS

<details open>
  <summary><strong>SWITCH EDIFÍCIO A</strong></summary>

  ```
  conf t
  vlan 10
   name ALUNOS_A
  vlan 20
   name PROFESSORES_A
  vlan 50
   name SERV_INFO
  vlan 60
   name CONVIDADOS_A
  vlan 70
   name TELEFONES_A
  vlan 80
   name IMPRESSORAS_A
  vlan 90
   name GESTAO_REDE_A
  vlan 99
   name PARKING_LOT
  exit
  write mem
  ```
</details>

<details open>
  <summary><strong>SWITCH EDIFÍCIO B</strong></summary>

``` 
conf t
vlan 11
 name ALUNOS_B
vlan 21
 name PROFESSORES_B
vlan 30
 name SERV_FINANCEIROS
vlan 40
 name SERV_ACADEMICOS
vlan 61
 name CONVIDADOS_B
vlan 71
 name TELEFONES_B
vlan 81
 name IMPRESSORAS_B
vlan 91
 name GESTAO_REDE_B
vlan 99
 name PARKING_LOT
end
write mem
```

</details>

<details open>
  <summary><strong>SWITCH DATACENTER</strong></summary>

``` 
conf t 
vlan 92
 name GESTAO_REDE_DATASET
vlan 93
 name DATACENTER
vlan 99
 name PARKING_LOT
end
write mem
```

</details>

## 3.2 TRUNK PORTS

Feito em Todas as Ligações Entre Switches

###  EDIFICIO A

<details open>
  <summary><strong>BASTIDOR 1</strong></summary>

```
------------ BASTIDOR 1 ------------

interface range ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

```
</details> 

<details open>
  <summary><strong>BASTIDOR 2</strong></summary>

```
------------ BASTIDOR 2 ------------ 

interface range ethernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

```
</details> 

<details open>
  <summary><strong>ENTRE BASTIDORES</strong></summary>

```
--------- ENTRE BASTIDORES ---------

------ SWITCH BA1-S3 E BA1-S4 ------

interface range ethernet1/2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

----------- SWITCH BA2-S1 ------------

interface range ethernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

----------- SWITCH BA2-S2 ------------
 
interface range ethernet1/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

```
</details> 


###  EDIFICIO B

<details open>
  <summary><strong>BASTIDOR 1</strong></summary>

```
------------ BASTIDOR 1 ------------

------ SWITCH BB1-S1 E BB1-S3 ------

interface range ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91

 ---------- SWITCH BB1-S5 ----------

interface range ethernet0/0 - 3 
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91

 ------ SWITCH BB1-S2; BB1-S4; BB1-S6 ------

interface range ethernet0/0 - 1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91

```
</details> 

<details open>
  <summary><strong>BASTIDOR 2</strong></summary>

```
------------ BASTIDOR 2 ------------
 
interface range ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
```
</details> 

<details open>
  <summary><strong>ENTRE BASTIDORES</strong></summary>

```
--------- ENTRE BASTIDORES ---------

interface range ethernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91

```
</details> 


### DATABASE 

<details open>
  <summary><strong>LAN DATACENTER</strong></summary>

```
------- LAN DATACENTER -------
interface Et0/0
 switchport trunk encapsulation dot1q     
 switchport mode trunk
 switchport trunk allowed vlan 92,93
exit

```
</details> 


## 3.3 ACCESS PORTS

Feito em Todas as Portas que ligam aos Equipamnetos Terminais e No Swictch LAN-Datacenter nas ligações aos servidores

<details open>
  <summary><strong>ACCESS PORTS</strong></summary>
  
```
------- ACCESS PORTS ------
Interface <interface id>
  switchport mode access
  switchport access vlan <vlan id>
exit

```
</details> 

## 3.4 PORTS PARKING (VLAN_PARKING_LOT)

Feito em Todas as Portas do Switch Inutilizadas (Adaptado ao Range necessário em cada Switch!)

<details open>
  <summary><strong>PORTS PARKING</strong></summary>
  
```
------- PORTS PARKING ------
interface range e0/0 - 3 , e1/0 - 3 , e2/0 - 3 , e3/0 - 3 , e4/0 - 3 , e5/0 - 3
 switchport mode access
 switchport access vlan 99
exit

show interfaces status
```

</details> 


# 4. Static Routing 

<details open>
  <summary><strong>ROUTER A</strong></summary>

```
------------ ROUTER A ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.1.2
exit
```
</details>

<details open>
  <summary><strong>ROUTER B</strong></summary>

```
------------ ROUTER B ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.2.2
exit
```
</details>


<details open>
  <summary><strong>ROUTER CENTRAL</strong></summary>

```
------------ ROUTER CENTRAL ------------

conf t
ip route 192.168.10.0 255.255.255.128 10.0.1.1
ip route 192.168.11.0 255.255.255.0 10.0.2.1
ip route 192.168.20.0 255.255.255.240 10.0.1.1
ip route 192.168.21.0 255.255.255.192 10.0.2.1
ip route 192.168.30.0 255.255.255.240 10.0.2.1
ip route 192.168.40.0 255.255.255.224 10.0.2.1
ip route 192.168.50.0 255.255.255.240 10.0.1.1
ip route 192.168.60.0 255.255.255.248 10.0.1.1
ip route 192.168.61.0 255.255.255.240 10.0.2.1
ip route 192.168.70.0 255.255.255.224 10.0.1.1
ip route 192.168.71.0 255.255.255.224 10.0.2.1
ip route 192.168.80.0 255.255.255.240 10.0.1.1
ip route 192.168.81.0 255.255.255.240 10.0.2.1
ip route 192.168.90.0 255.255.255.224 10.0.1.1
ip route 192.168.91.0 255.255.255.224 10.0.2.1
ip route 192.168.92.0 255.255.255.224 10.0.3.1
ip route 192.168.93.0 255.255.255.224 10.0.3.1
ip route 192.168.94.0 255.255.255.248 10.0.4.1
exit
```
</details>


<details open> 
  <summary><strong>ROUTER DATACENTER</strong></summary>

```
------------ ROUTER DATACENTER ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.3.2
exit
```
</details>


<details open>
  <summary><strong>ROUTER ISP</strong></summary>

```
------------ ROUTER ISP ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.4.2
IP route 10.0.0.0 255.255.255.248 10.0.4.2
exit
```
</details>


# 5. Router On-a-Stick - Edifício A 

<details open>
  <summary><strong>ROUTER A</strong></summary>

```bash

! Switch de Ligação colocar em trunk BA1-S1

interface e0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 
 
! VLAN 10 - ALUNOS_A
interface Ethernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.128

! VLAN 20 - PROFESSORES_A
interface Ethernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.240

! VLAN 50 - SINFO
interface Ethernet0/0.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.240 ---

! VLAN 60 - CONVIDADOS_A
interface Ethernet0/0.60
 encapsulation dot1Q 60 native
 ip address 192.168.60.1 255.255.255.248 ---

! VLAN 70 - TELEFONES_A
interface Ethernet0/0.70
 encapsulation dot1Q 70
 ip address 192.168.70.1 255.255.255.224

! VLAN 80 - IMPRESSORAS_A
interface Ethernet0/0.80
 encapsulation dot1Q 80
 ip address 192.168.80.1 255.255.255.240

! VLAN 90 - GESTÃO_REDE_A
interface Ethernet0/0.90
 encapsulation dot1Q 90
 ip address 192.168.90.1 255.255.255.224
```

</details> 

<details open>
  <summary><strong>ROUTER DATACENTER</strong></summary>

```

! Switch de Ligação colocar em trunk LAN-Datacenter

conf t
interface Et0/0
 switchport trunk encapsulation dot1q     
 switchport mode trunk
 switchport trunk allowed vlan 92,93
exit

interface Ethernet0/1.92
 encapsulation dot1Q 92
 ip address 192.168.92.1 255.255.255.224
 
 interface Ethernet0/1.93
 encapsulation dot1Q 93
 ip address 192.168.93.1 255.255.255.248
```

</details>


# 6. Legacy Inter-VLAN Routing 

<details open> 
  <summary><strong>ROUTER B</strong></summary>

```
interface Ethernet0/3
 ip address 192.168.11.1 255.255.255.0
 no shutdown

interface Ethernet1/0
 ip address 192.168.21.1 255.255.255.192
 no shutdown

interface Ethernet1/1
 ip address 192.168.30.1 255.255.255.240
 no shutdown

interface Ethernet1/2
 ip address 192.168.40.1 255.255.255.224
 no shutdown

interface Ethernet1/3
 ip address 192.168.61.1 255.255.255.248
 no shutdown

interface Ethernet2/0
 ip address 192.168.71.1 255.255.255.224
 no shutdown

interface Ethernet2/1
 ip address 192.168.81.1 255.255.255.248
 no shutdown

interface Ethernet2/2
 ip address 192.168.91.1 255.255.255.224
 no shutdown
````

</details> 

<details open>
  <summary><strong>SWITCH BB2-S6 </strong></summary>

```
interface Ethernet0/3
 switchport mode access
 switchport access vlan 11
exit
interface Ethernet1/0
 switchport mode access
 switchport access vlan 21
exit
interface Ethernet1/1
 switchport mode access
 switchport access vlan 30
exit
interface Ethernet1/2
 switchport mode access
 switchport access vlan 40
exit
interface Ethernet1/3
 switchport mode access
 switchport access vlan 61
exit
interface Ethernet2/0
 switchport mode access
 switchport access vlan 71
exit
interface Ethernet2/1
 switchport mode access
 switchport access vlan 81
exit
interface Ethernet2/2
 switchport mode access
 switchport access vlan 91
exit

interface vlan 91
 ip address 192.168.91.26 255.255.255.224
 no shutdown
exit

ip default-gateway 192.168.91.1

end
```

</details> 


# 7. Servidor DHCP (Router Datacenter) 


<details open>
  <summary><strong>ROUTER DATABASE</strong></summary>
  
```
conf t
ip dhcp excluded-address 10.0.1.1 10.0.1.2
ip dhcp excluded-address 10.0.2.1 10.0.2.2
ip dhcp excluded-address 10.0.3.1 10.0.3.2
ip dhcp excluded-address 10.0.4.1 10.0.4.2

ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.11.1
ip dhcp excluded-address 192.168.20.1
ip dhcp excluded-address 192.168.21.1
ip dhcp excluded-address 192.168.30.1
ip dhcp excluded-address 192.168.40.1
ip dhcp excluded-address 192.168.50.1
ip dhcp excluded-address 192.168.60.1
ip dhcp excluded-address 192.168.61.1
ip dhcp excluded-address 192.168.70.1
ip dhcp excluded-address 192.168.71.1
ip dhcp excluded-address 192.168.80.1
ip dhcp excluded-address 192.168.81.1
ip dhcp excluded-address 192.168.90.1
ip dhcp excluded-address 192.168.90.11 192.168.90.14
ip dhcp excluded-address 192.168.90.21 192.168.90.22
ip dhcp excluded-address 192.168.91.1
ip dhcp excluded-address 192.168.91.11 192.168.91.16
ip dhcp excluded-address 192.168.91.21 192.168.91.26
ip dhcp excluded-address 192.168.92.1
exit
```
```
conf t

ip dhcp pool POOL_ALUNOS_A
 network 192.168.10.0 255.255.255.128
 default-router 192.168.10.1
 dns-server 8.8.8.8

ip dhcp pool POOL_ALUNOS_B
 network 192.168.11.0 255.255.255.0
 default-router 192.168.11.1
 dns-server 8.8.8.8

ip dhcp pool POOL_PROF_A
 network 192.168.20.0 255.255.255.240
 default-router 192.168.20.1
 dns-server 8.8.8.8

ip dhcp pool POOL_PROF_B
 network 192.168.21.0 255.255.255.192
 default-router 192.168.21.1
 dns-server 8.8.8.8

ip dhcp pool POOL_FIN
 network 192.168.30.0 255.255.255.240
 default-router 192.168.30.1
 dns-server 8.8.8.8

ip dhcp pool POOL_ACA
 network 192.168.40.0 255.255.255.224
 default-router 192.168.40.1
 dns-server 8.8.8.8

ip dhcp pool POOL_SINFO
 network 192.168.50.0 255.255.255.240
 default-router 192.168.50.1
 dns-server 8.8.8.8

ip dhcp pool POOL_CONV_A
 network 192.168.60.0 255.255.255.248
 default-router 192.168.60.1
 dns-server 8.8.8.8

ip dhcp pool POOL_CONV_B
 network 192.168.61.0 255.255.255.240
 default-router 192.168.61.1
 dns-server 8.8.8.8

ip dhcp pool POOL_TEL_A
 network 192.168.70.0 255.255.255.224
 default-router 192.168.70.1
 dns-server 8.8.8.8

ip dhcp pool POOL_TEL_B
 network 192.168.71.0 255.255.255.224
 default-router 192.168.71.1
 dns-server 8.8.8.8

ip dhcp pool POOL_IMP_A
 network 192.168.80.0 255.255.255.240
 default-router 192.168.80.1
 dns-server 8.8.8.8

ip dhcp pool POOL_IMP_B
 network 192.168.81.0 255.255.255.240
 default-router 192.168.81.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_A
 network 192.168.90.0 255.255.255.224
 default-router 192.168.90.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_B
 network 192.168.91.0 255.255.255.224
 default-router 192.168.91.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_DATA
 network 192.168.92.0 255.255.255.224
 default-router 192.168.92.1
 dns-server 8.8.8.8

exit
```

</details> 


<details open> 
  <summary><strong>ROUTER A (Relay)</strong></summary>

```
conf t

interface e0/0.10
 ip helper-address 10.0.3.1
exit

interface e0/0.20
 ip helper-address 10.0.3.1
exit

interface e0/0.50
 ip helper-address 10.0.3.1
exit

interface e0/0.60
 ip helper-address 10.0.3.1
exit

interface e0/0.70
 ip helper-address 10.0.3.1
exit

interface e0/0.80
 ip helper-address 10.0.3.1
exit

interface e0/0.90
 ip helper-address 10.0.3.1
exit

write memory
```

</details> 

<details open>
  <summary><strong>ROUTER B (Relay)</strong></summary>

 ```
conf t
interface range e0/3 e1/0 - 3 e2/0 - 2
 ip helper-address 10.0.3.1
exit
```

</details> 


# 8. Redundância de L2 (Spanning Tree Protocol) 

## 8.2 EDIFICIO A 

<details open>
  <summary><strong>TODOS OS SWITCHES</strong></summary>
  
```
configure terminal
spanning-tree vlan 10
spanning-tree vlan 20
spanning-tree vlan 50
spanning-tree vlan 60
spanning-tree vlan 70
spanning-tree vlan 80
spanning-tree vlan 91
exit
```
</details> 

<details open>
  <summary><strong>BA1-S1 (ROOT BRIDGE)</strong></summary>

```
configure terminal
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
spanning-tree vlan 50 root primary
spanning-tree vlan 60 root primary
spanning-tree vlan 70 root primary
spanning-tree vlan 80 root primary
spanning-tree vlan 90 root primary
exit
```
</details> 

<details open>
  <summary><strong>BA1-S3 (ROOT SECONDARY)</strong></summary>

```
configure terminal
spanning-tree vlan 10 root secondary
spanning-tree vlan 20 root secondary
spanning-tree vlan 50 root secondary
spanning-tree vlan 60 root secondary
spanning-tree vlan 70 root secondary
spanning-tree vlan 80 root secondary
spanning-tree vlan 90 root secondary
exit
```
</details> 

<details open>
  <summary><strong>BA1-S2, BA1-S4, BA2-S1, BA2-S2 (OUTROS)</strong></summary>

```
configure terminal
spanning-tree vlan 10 priority 32768
spanning-tree vlan 20 priority 32768
spanning-tree vlan 50 priority 32768
spanning-tree vlan 60 priority 32768
spanning-tree vlan 70 priority 32768
spanning-tree vlan 80 priority 32768
spanning-tree vlan 90 priority 32768
exit
```
</details> 

## 8.1 EDIFICIO B 

<details open>
  <summary><strong>TODOS OS SWITCHES</strong></summary>

```
configure terminal
spanning-tree vlan 11
spanning-tree vlan 21
spanning-tree vlan 30
spanning-tree vlan 40
spanning-tree vlan 61
spanning-tree vlan 71
spanning-tree vlan 81
spanning-tree vlan 91
exit
```
</details> 

<details open> 
  <summary><strong>BB2-S6 (ROOT BRIDGE)</strong></summary>

```
configure terminal
spanning-tree vlan 11 priority 0
spanning-tree vlan 21 priority 0
spanning-tree vlan 30 priority 0
spanning-tree vlan 40 priority 0
spanning-tree vlan 61 priority 0
spanning-tree vlan 71 priority 0
spanning-tree vlan 81 priority 0
spanning-tree vlan 91 priority 0
exit
```
</details> 

<details open> 
  <summary><strong>BB1-S1 a S6, BB2-S1 a S5 (OUTROS)</strong></summary>

```
configure terminal
spanning-tree vlan 11 priority 32768
spanning-tree vlan 21 priority 32768
spanning-tree vlan 30 priority 32768
spanning-tree vlan 40 priority 32768
spanning-tree vlan 61 priority 32768
spanning-tree vlan 71 priority 32768
spanning-tree vlan 81 priority 32768
spanning-tree vlan 91 priority 32768
exit
```

</details> 

# 9. Implementação de Port Security

Deve Ser Feito em Todas as Interfaces em Modo Acesso

<details open> 
  <summary><strong>PORT-SECURITY</strong></summary>

```
conf t
interface range <interface id>
 switchport port-security
 switchport port-security maximum 1
 switchport port-security violation shutdown
 switchport port-security mac-address sticky
exit
```
</details> 

# 10. Segurança STP - (PORTFAST, BPDU GUARD, ROOT GUARD, LOOP GUARD)

## Mecanismos de Proteção no Spanning Tree Protocol (STP)

<details open> 
  <summary><strong>PORTFAST</strong></summary>


**O que faz:**  
PortFast é uma funcionalidade do Spanning Tree Protocol (STP) que permite que portas configuradas como "Access" (geralmente ligadas a dispositivos finais, como computadores ou impressoras) entrem diretamente no estado de "Forwarding". Isso reduz o tempo de espera para a porta começar a transmitir tráfego, evitando o atraso comum causado pela negociação do STP.

```
! Fazer nas Portas Access a equipamentos treminais

spanning-tree portfast
```
</details>

<details open> 
  <summary><strong>BPDU GUARD</strong></summary>

**O que faz:**  
O BPDU Guard é uma proteção contra dispositivos não autorizados que possam enviar BPDUs (Bridge Protocol Data Units) para portas configuradas com PortFast. Quando um BPDU é recebido em uma porta com BPDU Guard ativado, essa porta será colocada em estado de "errdisable" (desabilitada). Isso impede que switches ou outros dispositivos indesejados se conectem à rede e alterem a topologia da árvore de spanning.


```
! Fazer nas Portas Access a equipamentos treminais

spanning-tree bpduguard enable
```
</details>

<details open>
  <summary><strong>ROOT GUARD</strong></summary>

**O que faz:**  
O Root Guard é usado para proteger a rede contra a promoção indesejada de um switch para o papel de root bridge (ponte raiz) no protocolo Spanning Tree. Quando ativado em uma porta Designated, o Root Guard impede que um BPDU indicando um root bridge diferente seja aceito. Se isso ocorrer, a porta é colocada em estado "errdisable" para proteger a topologia.


```
! Fazer nas Portas Designated

spanning-tree guard root
```
</details>

<details open>
  <summary><strong>LOOP GUARD</strong></summary>

**O que faz:**  
O Loop Guard é uma proteção contra loops de rede. Ele é ativado nas portas que estão em estado "Blocked" ou "Alternate", que normalmente não deveriam encaminhar tráfego. Se uma dessas portas começar a enviar tráfego, o Loop Guard a coloca em estado de "errdisable", prevenindo a formação de loops na rede que possam causar degradação de desempenho ou falhas na comunicação.


```
! Fazer nas Portas Bloked/Alternate

spanning-tree guard loop
```
</details>

## PORT STATE (DESIGNATED, ROOT BRIDGE, BLOCK)

<details open>
  <summary><strong>EDIFICIO A</strong></summary>

```
------- BASTIDOR 1 ------

-SW1
    E0/0-3 designated (ROOT BRIDGE)
-SW2
    E0/0 root
    E0/1-2 block - LOOP GUARD
-SW3
    E0/0 designated - ROOT GUARD
    E0/1 root
    E0/2 designated - ROOT GUARD
    E1/2 designated - ROOT GUARD
-SW4
    E0/0 block - LOOP GUARD
    E0/1 designated - ROOT GUARD
    E0/2 root
    E1/2 designated - ROOT GUARD
 
------- BASTIDOR 2 ------

-SW1
    E0/0 designated - ROOT GUARD
    E0/3 root
-SW2
    E0/0 block - LOOP GUARD
    E1/0 root

```

</details>


<details open> 
  <summary><strong>EDIFICIO B</strong></summary>

```
------- BASTIDOR 1 ------

-SW1 
    E0/0 designated - ROOT GUARD
    E0/1 blocked    - LOOP GUARD
    E0/2 root
-SW2
    E0/0 block - LOOP GUARD
    E0/1 root
	
-SW3
    E0/0 designated - ROOT GUARD
    E0/1 root
    E0/2 designated - ROOT GUARD
-SW4
    E0/0 block - LOOP GUARD
    E0/1 designated - ROOT GUARD
    E0/3 root

-SW5
    E0/0 designated - ROOT GUARD
    E0/1 root
    E0/2 designated - ROOT GUARD
    E0/3 block - LOOP GUARD

-SW6 
	E0/1 designated - ROOT GUARD

------- BASTIDOR 2  ------

-SW1
    E0/0 root
    E0/1 designated - ROOT GUARD
    E0/2 block - LOOP GUARD
    E0/3 designated - ROOT GUARD

-SW2
    E0/0 designated - ROOT GUARD
    E0/1 designated - ROOT GUARD
    E0/2 root
    E0/3 designated - ROOT GUARD

-SW3
    E0/0 block - LOOP GUARD
    E0/1 root
    E0/2 block - LOOP GUARD
    E0/3 designated - ROOT GUARD

-SW4 
    E0/0 block - LOOP GUARD
    E0/1 block - LOOP GUARD
    E0/2 root

-SW5
    E0/0 designated - ROOT GUARD
    E0/1 root
    E0/2 designated - ROOT GUARD
	E0/3 designated - ROOT GUARD

-SW6
    Todas en designated (ROOT BRIDGE) 
```

</details>


# 11. ACL (Access Control List)

- Todas as ACLs foram atribuídas com o recurso 'in', já que devido às especificações da rede, era a melhor maneira de evitar o tráfego indesejado, proibindo-o na origem e descarregando possíveis pacotes que saturam a rede.

- Há uma ACL em cada VLAN do router dos edifícios, para distribuir o tráfego o mais segregado possível

- **No edifício A foi atribuido às subinterfaces**

<details open>
  <summary><strong>Exemplo</strong></summary>
	
```
interface e0/0.10
ip access-group ALUNOS_A in
```
</details> 

- **No edifício B, por ter a solução LEGACY, são aplicadas diretamente às interfaces**

<details open>
  <summary><strong>Exemplo</strong></summary>

```
interface e2/2
ip access-group GESTAO_B in
```
</details> 


## GENERAL

<details open>
  <summary><strong>GESTAO</strong></summary>
	
```
permit udp any host 10.0.3.1 eq 67 ! DHCP
permit ip 192.168.92.0 0.0.0.21 192.168.91.0 0.0.0.21
permit ip 192.168.92.0 0.0.0.21 192.168.90.0 0.0.0.21 
```
</details>

## EDIFICIO A

<details open> 
  <summary><strong>ALUNOS</strong></summary>

```
ip access-list extended ALUNOS_B
permit tcp any host 192.168.93.3 eq 80 ! HTTP inst
permit tcp any host 192.168.94.1 eq 80 ! Internet 1
permit tcp any host 192.168.94.1 eq 443 ! Internet 2
permit udp any host 255.255.255.255 eq 67 ! DHCP
permit ip 192.168.10.0 0.0.0.127 192.168.80.0 0.0.0.15 ! Impresoras
permit ip 192.168.10.0 0.0.0.127 192.168.11.0 0.0.0.255 ! Interedificios
```
</details>

<details open>
  <summary><strong>PROFESORES</strong></summary>
	
```
ip access-list extended PROFESORES_A
permit tcp any host 192.168.93.3 eq 80 ! HTTP inst
permit tcp any host 192.168.94.1 eq 80 ! Internet 1
permit tcp any host 192.168.94.1 eq 443 ! Internet 2
permit udp any host 255.255.255.255 eq 67 ! DHCP
permit tcp any host 192.168.93.4 eq 80 ! HTTP
permit ip 192.168.20.0 0.0.0.15 192.168.80.0 0.0.0.15 ! Impresoras
permit ip 192.168.20.0 0.0.0.15 192.168.21.0 0.0.0.63 ! Interedificios
```
</details>

<details open>
  <summary><strong>INFORMATICA</strong></summary>

```
ip access-list extended INFORMATICA
permit tcp any host 192.168.93.3 eq 80 ! HTTP inst
permit tcp any host 192.168.94.1 eq 80 ! Internet 1
permit tcp any host 192.168.94.1 eq 443 ! Internet 2
permit udp any host 255.255.255.255 eq 67 ! DHCP
permit tcp any host 192.168.93.4 eq 80 ! HTTP
permit ip 192.168.50.0 0.0.0.15 192.168.80.0 0.0.0.15 ! Impresoras
permit tcp any host 192.168.93.5 eq 21 ! FTP
```
</details>

<details open>
  <summary><strong>CONVIDADOS</strong></summary>
	
```
ip access-list extended CONVIDADOS_A
permit tcp any host 192.168.94.1 eq 80 ! Internet 1
permit tcp any host 192.168.94.1 eq 443 ! Internet 2
permit udp any host 192.168.60.1 eq 67 ! DHCP
permit udp any host 255.255.255.255 eq 67 ! DHCP
```

</details>

<details open>
  <summary><strong>IMPRESORAS</strong></summary>
	
```
ip access-list extended IMPRESORAS_A
permit udp any host 192.168.80.1 eq 67 ! DHCP
permit udp any host 255.255.255.255 eq 67 ! DHCP
```
</details>

<details open>
  <summary><strong>TELEFONES</strong></summary>

```
ip access-list extended TELEFONES_A
permit udp any host 192.168.70.1 eq 67 ! DHCP
permit udp any host 255.255.255.255 eq 67 ! DHCP
permit ip 192.168.70.0 0.0.0.31 192.168.71.0 0.0.0.31 ! Interedificios
```
</details>

<details open>
  <summary><strong>GESTAO</strong></summary>

```
permit udp any host 10.0.3.1 eq 67 ! DHCP
permit ip 192.168.90.0 0.0.0.21 192.168.91.0 0.0.0.21
permit ip 192.168.90.0 0.0.0.21 192.168.92.0 0.0.0.21 
```
</details>



## EDIFICIO B

<details open>
  <summary><strong>ALUNOS</strong></summary>
	
```
ip access-list extended ALUNOS_B

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 192.168.11.1 eq 67 ! DHCP

permit ip 192.168.11.0 0.0.0.255 192.168.80.0 0.0.0.15 ! Impresoras

permit ip 192.168.11.0 0.0.0.255 192.168.10.0 0.0.0.127 ! Interedificios
```
</details> 

<details open>
  <summary><strong>PROFESORES</strong></summary>
	
```
ip access-list extended PROFESORES_B

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 255.255.255.255 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.21.0 0.0.0.63 192.168.81.0 0.0.0.15 ! Impresoras

permit ip 192.168.21.0 0.0.0.63 192.168.20.0 0.0.0.15 ! Interedificios
```
</details>

<details open>
  <summary><strong>FINANCIEROS</strong></summary>
	
```
ip access-list extended FINANCIEROS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 255.255.255.255 eq 67 ! DHCP

permit ip 192.168.30.0 0.0.0.15 192.168.81.0 0.0.0.15 ! Impresoras
```
</details>


<details open> 
  <summary><strong>ACADEMICOS</strong></summary>

```
ip access-list extended ACADEMICOS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 255.255.255.255 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.40.0 0.0.0.31 192.168.81.0 0.0.0.15 ! Impresoras
```
</details>

<details open> 
  <summary><strong>CONVIDADOS</strong></summary>


```
ip access-list extended CONVIDADOS_B

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 255.255.255.255 eq 67 ! DHCP
```
</details>

<details open>
  <summary><strong>IMPRESORAS</strong></summary>

```
ip access-list extended IMPRESORAS_B

permit udp any host 255.255.255.255 eq 67 ! DHCP
```
</details>

<details open> 
  <summary><strong>TELEFONES</strong></summary>
	
```
ip access-list extended TELEFONES_B

permit udp any host 255.255.255.255 eq 67 ! DHCP

permit ip 192.168.71.0 0.0.0.31 192.168.70.0 0.0.0.31 ! Interedificios
```
</details>

<details open>
  <summary><strong>GESTAO</strong></summary>
	
```
permit udp any host 10.0.3.1 eq 67 ! DHCP
permit ip 192.168.91.0 0.0.0.21 192.168.90.0 0.0.0.21
permit ip 192.168.91.0 0.0.0.21 192.168.92.0 0.0.0.21 
```
</details>


# SHOW RUN´S

# EDIFICIO A

<details>
  <summary><strong>BA1-S1</strong></summary>

```
BA1-S1#show run
Building configuration...

Current configuration : 4926 bytes
!
! Last configuration change at 18:29:10 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA1-S1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 10,20,50,60,70,80,90 priority 24576
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport access vlan 99
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
!
interface Ethernet1/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.11 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
````
</details>
<details>
  <summary><strong>BA1-S2</strong></summary>

```
BA1-S2#show run
Building configuration...

Current configuration : 4994 bytes
!
! Last configuration change at 18:29:27 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA1-S2
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/3
 switchport access vlan 50
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 50
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 50
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 50
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 50
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.12 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BA1-S3</strong></summary>
	
```
BA1-S3#show run
Building configuration...

Current configuration : 5364 bytes
!
! Last configuration change at 18:29:13 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA1-S3
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 10,20,50,60,70,80,90 priority 28672
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/3
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6805
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6800
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6807
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/3
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.13 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BA1-S4</strong></summary>
	
```
BA1-S4#show run
Building configuration...

Current configuration : 5349 bytes
!
! Last configuration change at 18:29:13 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA1-S4
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6802
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport access vlan 60
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6804
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6808
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/3
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 80
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.14 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BA2-S1</strong></summary>

```
BA2-S1#show run
Building configuration...

Current configuration : 5426 bytes
!
! Last configuration change at 18:29:14 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA2-S1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Port-channel1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 channel-group 1 mode active
 spanning-tree guard root
!
interface Ethernet0/1
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6809
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet0/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6814
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet0/3
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet1/0
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.681a
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 1 mode active
!
interface Ethernet5/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.21 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BA2-S2</strong></summary>

```
BA2-S2#show run
Building configuration...

Current configuration : 5439 bytes
!
! Last configuration change at 18:29:16 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BA2-S2
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Port-channel1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
 duplex full
 channel-group 1 mode active
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6806
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet0/2
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.680e
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet0/3
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.681b
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 60
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet1/1
 switchport access vlan 20
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 70
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 10
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 switchport trunk encapsulation dot1q
 switchport mode trunk
 channel-group 1 mode active
!
interface Ethernet5/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan90
 ip address 192.168.90.22 255.255.255.224
!
ip default-gateway 192.168.90.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.90.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>EDF.A-R1</strong></summary>

```
DF.A-R1#show run
Building configuration...

Current configuration : 5226 bytes
!
version 15.7
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname EDF.A-R1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
!
!
!
!
!
!
!


!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
redundancy
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 no ip address
 duplex auto
!
interface Ethernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.128
 ip access-group ALUNOS_A in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.240
 ip access-group PROFESORES_B in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.240
 ip access-group INFORMATICA in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.60
 encapsulation dot1Q 60 native
 ip address 192.168.60.1 255.255.255.248
 ip access-group CONVIDADOS_A in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.70
 encapsulation dot1Q 70
 ip address 192.168.70.1 255.255.255.224
 ip access-group TELEFONES_A in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.80
 encapsulation dot1Q 80
 ip address 192.168.80.1 255.255.255.240
 ip access-group IMPRESORAS_A in
 ip helper-address 10.0.3.1
!
interface Ethernet0/0.90
 encapsulation dot1Q 90
 ip address 192.168.90.1 255.255.255.224
 ip access-group GESTAO_A in
 ip helper-address 10.0.3.1
!
interface Ethernet0/1
 ip address 10.0.1.1 255.255.255.252
 duplex auto
!
interface Ethernet0/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet0/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/3
 no ip address
 shutdown
 duplex auto
!
interface Serial4/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/3
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/3
 no ip address
 shutdown
 serial restart-delay 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 10.0.1.2
!
ip access-list extended ALUNOS_A
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
 permit ip 192.168.10.0 0.0.0.127 192.168.80.0 0.0.0.15
 permit ip 192.168.10.0 0.0.0.127 192.168.11.0 0.0.0.255
ip access-list extended CONVIDADOS_A
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended GESTAO_A
 permit udp any host 10.0.3.1 eq bootps
 permit ip 192.168.90.0 0.0.0.21 192.168.91.0 0.0.0.21
 permit ip 192.168.90.0 0.0.0.21 192.168.92.0 0.0.0.21
ip access-list extended IMPRESORAS_A
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended INFORMATICA
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit tcp any host 192.168.93.4 eq www
 permit ip 192.168.50.0 0.0.0.15 192.168.80.0 0.0.0.15
 permit tcp any host 192.168.93.5 eq ftp
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended PROFESORES_A
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit tcp any host 192.168.93.4 eq www
 permit ip 192.168.20.0 0.0.0.15 192.168.80.0 0.0.0.15
 permit ip 192.168.20.0 0.0.0.15 192.168.21.0 0.0.0.63
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended TELEFONES_A
 permit ip 192.168.70.0 0.0.0.31 192.168.71.0 0.0.0.31
 permit udp any host 255.255.255.255 eq bootps
!
ipv6 ioam timestamp
!
!
!
control-plane
!
!
!
!
!
!
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
 transport input none
!
!
end

```
</details>

# EDIFICIO B

<details>
  <summary><strong>BB1-S1</strong></summary>

```
BB1-S1#show run
Building configuration...

Current configuration : 5028 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport access vlan 99
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6816
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport access vlan 71
 switchport mode access
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.11 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>BB1-S2</strong></summary>

```
BB1-S2#show run
Building configuration...

Current configuration : 4997 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S2
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport access vlan 11
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet0/3
 switchport access vlan 11
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet1/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.12 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```

</details>

<details>
  <summary><strong>BB1-S3</strong></summary>
	
```
BB1-S3#show run
Building configuration...

Current configuration : 4819 bytes
!
! Last configuration change at 18:29:08 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S3
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet1/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.13 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```

</details>

<details>
  <summary><strong>BB1-S4</strong></summary>

```
BB1-S4#show run
Building configuration...

Current configuration : 5251 bytes
!
! Last configuration change at 18:29:08 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S4
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/2
 switchport access vlan 21
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet1/0
 switchport access vlan 21
 switchport mode access
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6812
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6813
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.14 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BB1-S5</strong></summary>

```
BB1-S5#show run
Building configuration...

Current configuration : 4899 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S5
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet1/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet1/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.15 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>BB1-S6</strong></summary>

```
BB1-S6#show run
Building configuration...

Current configuration : 4948 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB1-S6
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/2
 switchport access vlan 11
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet1/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet1/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.16 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>


<details>
  <summary><strong>BB2-S1</strong></summary>
	
```
BB2-S1#show run
Building configuration...

Current configuration : 5353 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6800
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.680b
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6818
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/3
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 81
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet5/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.21 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
```
</details>

<details>
  <summary><strong>BB2-S2</strong></summary>
	
```
BB2-S2#show run
Building configuration...

Current configuration : 4928 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S2
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6803
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6818
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 40
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 40
 switchport mode access
!
interface Ethernet5/1
 switchport access vlan 40
 switchport mode access
!
interface Ethernet5/2
 switchport access vlan 40
 switchport mode access
!
interface Ethernet5/3
 switchport access vlan 40
 switchport mode access
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.22 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
	
```	
</details>

<details>
  <summary><strong>BB2-S3</strong></summary>

```
BB2-S3#show run
Building configuration...

Current configuration : 5333 bytes
!
! Last configuration change at 18:29:20 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S3
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/0
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.681f
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.680e
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6802
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/3
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 61
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.23 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>BB2-S4</strong></summary>

```
BB2-S4#show run
Building configuration...

Current configuration : 5122 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S4
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard loop
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport access vlan 21
 switchport mode access
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.680f
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.680a
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 21
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.24 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>BB2-S5</strong></summary>

```
BB2-S5#show run
Building configuration...

Current configuration : 5212 bytes
!
! Last configuration change at 18:29:12 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S5
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet0/3
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
 spanning-tree guard root
!
interface Ethernet1/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.6811
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/1
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0050.7966.681a
 switchport port-security
 spanning-tree portfast edge
 spanning-tree bpduguard enable
!
interface Ethernet1/2
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet1/3
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/0
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/1
 switchport access vlan 71
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/2
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet2/3
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/0
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/1
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/2
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet3/3
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/0
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 30
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan91
 ip address 192.168.91.25 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details>
  <summary><strong>BB2-S6</strong></summary>

```
BB2-S6#show run
Building configuration...

Current configuration : 3791 bytes
!
! Last configuration change at 18:29:09 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname BB2-S6
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
spanning-tree vlan 11,21,30,40,61,71,81,91 priority 0
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/1
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/2
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet0/3
 switchport access vlan 11
 switchport mode access
!
interface Ethernet1/0
 switchport access vlan 21
 switchport mode access
!
interface Ethernet1/1
 switchport access vlan 30
 switchport mode access
!
interface Ethernet1/2
 switchport access vlan 40
 switchport mode access
!
interface Ethernet1/3
 switchport access vlan 61
 switchport mode access
!
interface Ethernet2/0
 switchport access vlan 71
 switchport mode access
!
interface Ethernet2/1
 switchport access vlan 81
 switchport mode access
!
interface Ethernet2/2
 switchport access vlan 91
 switchport mode access
!
interface Ethernet2/3
 switchport access vlan 99
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 switchport trunk encapsulation dot1q
 switchport trunk native vlan 61
 switchport mode trunk
 switchport nonegotiate
!
interface Ethernet3/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet3/1
 switchport access vlan 11
 switchport mode access
!
interface Ethernet3/2
 switchport access vlan 11
 switchport mode access
!
interface Ethernet3/3
 switchport access vlan 11
 switchport mode access
!
interface Ethernet4/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet4/1
 switchport access vlan 11
 switchport mode access
!
interface Ethernet4/2
 switchport access vlan 11
 switchport mode access
!
interface Ethernet4/3
 switchport access vlan 11
 switchport mode access
!
interface Ethernet5/0
 switchport access vlan 11
 switchport mode access
!
interface Ethernet5/1
 switchport access vlan 11
 switchport mode access
!
interface Ethernet5/2
 switchport access vlan 11
 switchport mode access
!
interface Ethernet5/3
 switchport access vlan 11
 switchport mode access
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan11
 no ip address
!
interface Vlan21
 no ip address
!
interface Vlan30
 no ip address
!
interface Vlan40
 no ip address
!
interface Vlan61
 no ip address
!
interface Vlan71
 no ip address
!
interface Vlan81
 no ip address
!
interface Vlan91
 ip address 192.168.91.26 255.255.255.224
!
ip default-gateway 192.168.91.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.91.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end

```
</details>

<details >
  <summary><strong>EDF.B-R1</strong></summary>

```
EDF.B-R1#show run
Building configuration...

Current configuration : 5102 bytes
!
! Last configuration change at 18:30:26 UTC Wed Oct 22 2025
!
version 15.7
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname EDF.B-R1
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
!
!
!
!
!
!
!


!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
redundancy
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 ip address 10.0.2.1 255.255.255.252
 duplex auto
!
interface Ethernet0/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet0/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet0/3
 ip address 192.168.11.1 255.255.255.0
 ip access-group ALUNOS_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet1/0
 ip address 192.168.21.1 255.255.255.192
 ip access-group PROFESORES_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet1/1
 ip address 192.168.30.1 255.255.255.240
 ip access-group FINANCIEROS in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet1/2
 ip address 192.168.40.1 255.255.255.224
 ip access-group ACADEMICOS in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet1/3
 ip address 192.168.61.1 255.255.255.248
 ip access-group CONVIDADOS_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet2/0
 ip address 192.168.71.1 255.255.255.224
 ip access-group TELEFONES_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet2/1
 ip address 192.168.81.1 255.255.255.248
 ip access-group IMPRESORAS_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet2/2
 ip address 192.168.91.1 255.255.255.224
 ip access-group GESTAO_B in
 ip helper-address 10.0.3.1
 duplex auto
!
interface Ethernet2/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/3
 no ip address
 shutdown
 duplex auto
!
interface Serial4/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/3
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/3
 no ip address
 shutdown
 serial restart-delay 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 10.0.2.2
!
ip access-list extended ACADEMICOS
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
 permit tcp any host 192.168.93.4 eq www
 permit ip 192.168.40.0 0.0.0.31 192.168.81.0 0.0.0.15
ip access-list extended ALUNOS_B
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit ip 192.168.11.0 0.0.0.255 192.168.80.0 0.0.0.15
 permit ip 192.168.11.0 0.0.0.255 192.168.10.0 0.0.0.127
 permit udp any host 192.168.11.1 eq bootps
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended CONVIDADOS_B
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended FINANCIEROS
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
 permit ip 192.168.30.0 0.0.0.15 192.168.81.0 0.0.0.15
ip access-list extended GESTAO_B
 permit udp any host 255.255.255.255 eq bootps
 permit ip 192.168.91.0 0.0.0.21 192.168.90.0 0.0.0.21
 permit ip 192.168.91.0 0.0.0.21 192.168.92.0 0.0.0.21
ip access-list extended IMPRESORAS_B
 permit udp any host 255.255.255.255 eq bootps
ip access-list extended PROFESORES_B
 permit tcp any host 192.168.93.3 eq www
 permit tcp any host 192.168.94.1 eq www
 permit tcp any host 192.168.94.1 eq 443
 permit udp any host 255.255.255.255 eq bootps
 permit tcp any host 192.168.93.4 eq www
 permit ip 192.168.21.0 0.0.0.63 192.168.81.0 0.0.0.15
 permit ip 192.168.21.0 0.0.0.63 192.168.20.0 0.0.0.15
ip access-list extended TELEFONES_B
 permit udp any host 255.255.255.255 eq bootps
 permit ip 192.168.71.0 0.0.0.31 192.168.70.0 0.0.0.31
!
ipv6 ioam timestamp
!
!
!
control-plane
!
!
!
!
!
!
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
 transport input none
!
!
end

```
</details>

# DATACENTER

<details>
  <summary><strong>LAN-DATACENTER</strong></summary>

````
LAN-DATACENTER#show run
Building configuration...

Current configuration : 4992 bytes
!
! Last configuration change at 18:29:18 UTC Wed Oct 22 2025
!
version 15.2
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
service compress-config
!
hostname LAN-DATACENTER
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
no ip domain-lookup
ip cef
no ipv6 cef
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
!
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 switchport trunk allowed vlan 92,93
 switchport trunk encapsulation dot1q
 switchport mode trunk
 spanning-tree guard root
!
interface Ethernet0/1
 switchport access vlan 93
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0242.b0ae.9000
 switchport port-security
 spanning-tree guard loop
!
interface Ethernet0/2
 switchport access vlan 93
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0242.f109.7100
 switchport port-security
 spanning-tree guard loop
!
interface Ethernet0/3
 switchport access vlan 93
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security mac-address sticky 0242.73bb.7000
 switchport port-security
 spanning-tree guard loop
!
interface Ethernet1/0
 switchport access vlan 99
 switchport mode access
 shutdown
!
interface Ethernet1/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet1/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet1/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet2/0
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet2/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet2/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet2/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet3/0
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet3/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet3/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet3/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
 shutdown
!
interface Ethernet4/0
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet4/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/0
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/1
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/2
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Ethernet5/3
 switchport access vlan 99
 switchport mode access
 switchport port-security mac-address sticky
 switchport port-security
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan92
 ip address 192.168.92.2 255.255.255.224
!
ip default-gateway 192.168.92.1
ip forward-protocol nd
!
ip tcp synwait-time 5
ip http server
!
ip route 0.0.0.0 0.0.0.0 192.168.92.1
ip ssh server algorithm encryption aes128-ctr aes192-ctr aes256-ctr
ip ssh client algorithm encryption aes128-ctr aes192-ctr aes256-ctr
!
!
!
!
!
control-plane
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
!
!
!
end
````
</details>

<details>
  <summary><strong>R-DATACENTER</strong></summary>

```
R-DATACENTER#show run
Building configuration...

Current configuration : 5851 bytes
!
version 15.7
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname R-DATACENTER
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
!
!
!
!
!
!
!


!
ip dhcp excluded-address 10.0.1.1 10.0.1.2
ip dhcp excluded-address 10.0.2.1 10.0.2.2
ip dhcp excluded-address 10.0.3.1 10.0.3.2
ip dhcp excluded-address 10.0.4.1 10.0.4.2
ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.11.1
ip dhcp excluded-address 192.168.20.1
ip dhcp excluded-address 192.168.21.1
ip dhcp excluded-address 192.168.30.1
ip dhcp excluded-address 192.168.40.1
ip dhcp excluded-address 192.168.50.1
ip dhcp excluded-address 192.168.60.1
ip dhcp excluded-address 192.168.61.1
ip dhcp excluded-address 192.168.70.1
ip dhcp excluded-address 192.168.71.1
ip dhcp excluded-address 192.168.80.1
ip dhcp excluded-address 192.168.81.1
ip dhcp excluded-address 192.168.90.1
ip dhcp excluded-address 192.168.90.11 192.168.90.14
ip dhcp excluded-address 192.168.90.21 192.168.90.22
ip dhcp excluded-address 192.168.91.1
ip dhcp excluded-address 192.168.91.11 192.168.91.16
ip dhcp excluded-address 192.168.92.1
ip dhcp excluded-address 192.168.91.21 192.168.91.27
!
ip dhcp pool POOL_ALUNOS_A
 network 192.168.10.0 255.255.255.128
 default-router 192.168.10.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_ALUNOS_B
 network 192.168.11.0 255.255.255.0
 default-router 192.168.11.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_PROF_A
 network 192.168.20.0 255.255.255.240
 default-router 192.168.20.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_PROF_B
 network 192.168.21.0 255.255.255.192
 default-router 192.168.21.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_FIN
 network 192.168.30.0 255.255.255.240
 default-router 192.168.30.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_ACA
 network 192.168.40.0 255.255.255.224
 default-router 192.168.40.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_SINFO
 network 192.168.50.0 255.255.255.240
 default-router 192.168.50.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_CONV_A
 network 192.168.60.0 255.255.255.248
 default-router 192.168.60.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_CONV_B
 network 192.168.61.0 255.255.255.240
 default-router 192.168.61.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_TEL_A
 network 192.168.70.0 255.255.255.224
 default-router 192.168.70.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_TEL_B
 network 192.168.71.0 255.255.255.224
 default-router 192.168.71.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_IMP_A
 network 192.168.80.0 255.255.255.240
 default-router 192.168.80.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_IMP_B
 network 192.168.81.0 255.255.255.240
 default-router 192.168.81.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_GEST_A
 network 192.168.90.0 255.255.255.224
 default-router 192.168.90.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_GEST_B
 network 192.168.91.0 255.255.255.224
 default-router 192.168.91.1
 dns-server 8.8.8.8
!
ip dhcp pool POOL_GEST_DATA
 network 192.168.92.0 255.255.255.224
 default-router 192.168.92.1
 dns-server 8.8.8.8
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
redundancy
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 ip address 10.0.3.1 255.255.255.252
 duplex auto
!
interface Ethernet0/0.92
 ip access-group GESTAO_GENERAL in
!
interface Ethernet0/1
 no ip address
 duplex auto
!
interface Ethernet0/1.92
 encapsulation dot1Q 92
 ip address 192.168.92.1 255.255.255.224
!
interface Ethernet0/1.93
 encapsulation dot1Q 93
 ip address 192.168.93.1 255.255.255.248
!
interface Ethernet0/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet0/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/3
 no ip address
 shutdown
 duplex auto
!
interface Serial4/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/3
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/3
 no ip address
 shutdown
 serial restart-delay 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 10.0.3.2
!
ip access-list extended GESTAO_GENERAL
 permit udp any host 10.0.3.1 eq bootps
 permit ip 192.168.92.0 0.0.0.21 192.168.91.0 0.0.0.21
 permit ip 192.168.92.0 0.0.0.21 192.168.90.0 0.0.0.21
!
ipv6 ioam timestamp
!
!
!
control-plane
!
!
!
!
!
!
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
 transport input none
!
!
end

```
</details>

<details>
  <summary><strong>R-CENTRAL</strong></summary>

```
R-CENTRAL#show run
Building configuration...

Current configuration : 3425 bytes
!
version 15.7
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname R-CENTRAL
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
!
!
!
!
!
!
!


!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
redundancy
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 ip address 10.0.1.2 255.255.255.252
 duplex auto
!
interface Ethernet0/1
 ip address 10.0.2.2 255.255.255.252
 duplex auto
!
interface Ethernet0/2
 ip address 10.0.3.2 255.255.255.252
 duplex auto
!
interface Ethernet0/3
 ip address 10.0.4.2 255.255.255.252
 duplex auto
!
interface Ethernet1/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/3
 no ip address
 shutdown
 duplex auto
!
interface Serial4/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/3
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/3
 no ip address
 shutdown
 serial restart-delay 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 192.168.10.0 255.255.255.128 10.0.1.1
ip route 192.168.11.0 255.255.255.0 10.0.2.1
ip route 192.168.20.0 255.255.255.240 10.0.1.1
ip route 192.168.21.0 255.255.255.192 10.0.2.1
ip route 192.168.30.0 255.255.255.240 10.0.2.1
ip route 192.168.40.0 255.255.255.224 10.0.2.1
ip route 192.168.50.0 255.255.255.240 10.0.1.1
ip route 192.168.60.0 255.255.255.248 10.0.1.1
ip route 192.168.61.0 255.255.255.240 10.0.2.1
ip route 192.168.70.0 255.255.255.224 10.0.1.1
ip route 192.168.71.0 255.255.255.224 10.0.2.1
ip route 192.168.80.0 255.255.255.240 10.0.1.1
ip route 192.168.81.0 255.255.255.240 10.0.2.1
ip route 192.168.90.0 255.255.255.224 10.0.1.1
ip route 192.168.91.0 255.255.255.224 10.0.2.1
ip route 192.168.92.0 255.255.255.224 10.0.3.1
ip route 192.168.93.0 255.255.255.224 10.0.3.1
ip route 192.168.94.0 255.255.255.248 10.0.4.1
!
ipv6 ioam timestamp
!
!
!
control-plane
!
!
!
!
!
!
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
 transport input none
!
!
end
```
</details>

<details>
  <summary><strong>R-ISP</strong></summary>

```
R-ISP#show run
Building configuration...

Current configuration : 2634 bytes
!
version 15.7
service timestamps debug datetime msec
service timestamps log datetime msec
no service password-encryption
!
hostname R-ISP
!
boot-start-marker
boot-end-marker
!
!
logging discriminator EXCESS severity drops 6 msg-body drops EXCESSCOLL
logging buffered 50000
logging console discriminator EXCESS
!
no aaa new-model
!
!
!
mmi polling-interval 60
no mmi auto-configure
no mmi pvc
mmi snmp-timeout 180
!
!
!
!
!
no ip icmp rate-limit unreachable
!
!
!
!
!
!
!
!
!
!


!
!
!
!
no ip domain lookup
ip cef
no ipv6 cef
!
multilink bundle-name authenticated
!
!
!
!
!
!
!
!
!
!
redundancy
!
!
ip tcp synwait-time 5
!
!
!
!
!
!
!
!
!
!
!
!
!
interface Ethernet0/0
 ip address 10.0.4.1 255.255.255.248
 duplex auto
!
interface Ethernet0/1
 ip address 192.168.94.1 255.255.255.248
 duplex auto
!
interface Ethernet0/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet0/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet1/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet2/3
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/0
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/1
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/2
 no ip address
 shutdown
 duplex auto
!
interface Ethernet3/3
 no ip address
 shutdown
 duplex auto
!
interface Serial4/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial4/3
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/0
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/1
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/2
 no ip address
 shutdown
 serial restart-delay 0
!
interface Serial5/3
 no ip address
 shutdown
 serial restart-delay 0
!
ip forward-protocol nd
!
!
no ip http server
no ip http secure-server
ip route 0.0.0.0 0.0.0.0 10.0.4.2
ip route 10.0.0.0 255.255.255.248 10.0.4.2
!
ipv6 ioam timestamp
!
!
!
control-plane
!
!
!
!
!
!
!
!
line con 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line aux 0
 exec-timeout 0 0
 privilege level 15
 logging synchronous
line vty 0 4
 login
 transport input none
!
!
end

```
</details>


