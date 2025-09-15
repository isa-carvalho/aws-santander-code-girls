# Desafio de projeto - Gerenciando Instâncias Ec2 na AWS


## &#x1F528; Objetivo do Desafio 
- Abordar a funcionalidade do serviço EC2 e como se conecta com outros serviços **(EBS,S3,Lambda).**
- Consolidar os conceitos aprendidos em um ambiente prático; 
- Documentar processos técnicos de forma clara e estruturada;
- Praticar a criação de diagramas de arquitetura na prática com a ferramenta Draw.io.

---

## &#x1F4D6; Conhecimentos Aprendidos

### &#x1F4BB; EC2 (elastic Compute Cloud)
É o serviço da AWS que permite criar máquinas virtuais na nuvem.

#### **Tipos de instâncias EC2:** 
Existem categorias de instâncias EC2 e como elas podemos definir qual modelo se ajusta ao uso e assim reduzir custos desnecessários e maximizar desempenho de acordo com a carga de trabalho:

| Tipo | Família | Uso |
|------|----------|-----|
| General Purpose | t3, t4g, m5 | Uso geral |
| Compute Optimized | c5, c6g | Processamento intenso |
| Memory Optimized | r5, x1e | Aplicações que precisam de muita memória |
| Storage Optimized | i3, d2, h1 | Grandes volumes de armazenamento |
| Accelerated Computing | p4, g5, f1 | Machine learning, gráficos, processamento acelerado |


#### AMI (Amazon Machine Image)
É uma imagem de maquina virutal pré-configurada, que inclui as informações necessarias para iniciar uma instância, como sistemas operativos, servidores de aplicações e suas aplicações.
    
#### **Armazenamento de uma Instância EC2**

- **EBS(Elastic Block Store)** → armazenamento persistente ligado à instância.
- **Instance Store** → armazenamento temporário.
- **EFS(Elastic File System)** → é um armazenamento de arquivos compartilhado,persistente e escalável, ideal para múltiplas instâncias EC2 acessarem ao mesmo tempo.

#### Snapshot de EC2
Snapshot é uma **fotografia** da sua instância que permite replicá-la facilmente na AWS. Isso facilita na recuperação de servidores de produção.

#### Snapshoot com EBS 
Cópias pontuais de volumes ou instâncias, que permitem recuperação rápida e replicação.

---

### S3(Simple Storage Service)
Serviço de armazenamento de objetos em nuvem oferecido pela AWS. È ideal para armaenar,organizar e recuperar grandes volumes de dados dr forma segura e escalavel.

---

## Diagrama

[Diagrama](link)

### Fluxo

O usuário acessa o blog, que está hospedado em uma instância EC2 (por exemplo, usando Nginx ou Apache). Essa instância utiliza um EBS para armazenar os dados dinâmicos de forma persistente e um S3 para gerenciar os arquivos estáticos, como imagens e scripts.

Sempre que há alterações no conteúdo do blog — como novas postagens ou adição de imagens — o Lambda é acionado a partir de eventos no S3, permitindo executar ações automáticas, como atualização de cache ou notificações. Além disso, outra trigger no Lambda monitora o EBS para automatizar backups dos dados dinâmicos, garantindo que nada seja perdido.