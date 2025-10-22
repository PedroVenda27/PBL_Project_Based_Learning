
# PBL_Project_Based_Learning

Este repositório documenta o projeto final colaborativo **"PBL - Project-Based Learning"**, desenvolvido no contexto das disciplinas **Comunicação de Dados e Redes II** e **Segurança de Redes e Sistemas**. O objetivo do projeto foi o planeamento, configuração e implementação de uma topologia de rede para um campus universitário, com a devida aplicação de medidas de segurança, realizado no curso de Informática (2.º ano) da UMAIA.

Aqui serão registados todos os passos do desenvolvimento do projeto, desde o enunciado e explicações iniciais até à definição da rede, configurações técnicas implementadas e as soluções de segurança adotadas. O repositório tem como objetivo proporcionar uma visão detalhada do processo, com foco na construção de uma infraestrutura de rede segura, eficiente e alinhada aos requisitos técnicos especificados no PDF fornecido.

---

# Enunciado do Projeto 

[PBL_Enunciado](./PBL_Enunciado) 

---

# Desenvolvimento

# 1. Topologia física e lógica 

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




# 3. VLANs

## 3.1 CRIAR VLANS

<details>
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
  <summary><strong>ROUTER A</strong></summary>

```
------------ ROUTER A ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.1.2
exit
```
</details>

<details> 
  <summary><strong>ROUTER B</strong></summary>

```
------------ ROUTER B ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.2.2
exit
```
</details>


<details> 
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


<details> 
  <summary><strong>ROUTER DATACENTER</strong></summary>

```
------------ ROUTER DATACENTER ------------

conf t
ip route 0.0.0.0 0.0.0.0 10.0.3.2
exit
```
</details>


<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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


<details> 
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


<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
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

<details> 
  <summary><strong>PORTFAST</strong></summary>


**O que faz:**  
PortFast é uma funcionalidade do Spanning Tree Protocol (STP) que permite que portas configuradas como "Access" (geralmente ligadas a dispositivos finais, como computadores ou impressoras) entrem diretamente no estado de "Forwarding". Isso reduz o tempo de espera para a porta começar a transmitir tráfego, evitando o atraso comum causado pela negociação do STP.

```
! Fazer nas Portas Access a equipamentos treminais

spanning-tree portfast
```
</details>

<details> 
  <summary><strong>BPDU GUARD</strong></summary>

**O que faz:**  
O BPDU Guard é uma proteção contra dispositivos não autorizados que possam enviar BPDUs (Bridge Protocol Data Units) para portas configuradas com PortFast. Quando um BPDU é recebido em uma porta com BPDU Guard ativado, essa porta será colocada em estado de "errdisable" (desabilitada). Isso impede que switches ou outros dispositivos indesejados se conectem à rede e alterem a topologia da árvore de spanning.


```
! Fazer nas Portas Access a equipamentos treminais

spanning-tree bpduguard enable
```
</details>

<details> 
  <summary><strong>ROOT GUARD</strong></summary>

**O que faz:**  
O Root Guard é usado para proteger a rede contra a promoção indesejada de um switch para o papel de root bridge (ponte raiz) no protocolo Spanning Tree. Quando ativado em uma porta Designated, o Root Guard impede que um BPDU indicando um root bridge diferente seja aceito. Se isso ocorrer, a porta é colocada em estado "errdisable" para proteger a topologia.


```
! Fazer nas Portas Designated

spanning-tree guard root
```
</details>

<details> 
  <summary><strong>LOOP GUARD</strong></summary>

**O que faz:**  
O Loop Guard é uma proteção contra loops de rede. Ele é ativado nas portas que estão em estado "Blocked" ou "Alternate", que normalmente não deveriam encaminhar tráfego. Se uma dessas portas começar a enviar tráfego, o Loop Guard a coloca em estado de "errdisable", prevenindo a formação de loops na rede que possam causar degradação de desempenho ou falhas na comunicação.


```
! Fazer nas Portas Bloked/Alternate

spanning-tree guard loop
```
</details>

## PORT STATE (DESIGNATED, ROOT BRIDGE, BLOCK)

<details> 
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


<details> 
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


