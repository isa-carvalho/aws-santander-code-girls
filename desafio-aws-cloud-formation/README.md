### AWS CloudFormation

O AWS CloudFormation é um serviço fundamental que permite modelar e provisionar a infraestrutura da AWS de forma **declarativa**, usando o conceito de **Infraestrutura como Código (IaC)**.

| Conceito | Descrição Técnica |
| :--- | :--- |
| **Definição** | Serviço de **Infraestrutura como Código (IaC)** que permite provisionar e gerenciar recursos da AWS de maneira organizada e previsível, usando arquivos de modelo. |
| **Modelo (Template)** | Arquivo de texto, geralmente em formato **YAML** ou **JSON**, que define o estado desejado dos recursos da AWS. É a planta da infraestrutura. |
| **Pilha (Stack)** | É a coleção de recursos da AWS criados e gerenciados como uma única unidade através de um modelo do CloudFormation. O CloudFormation rastreia e gerencia as dependências entre os recursos da pilha. |
| **Recursos (Resources)** | Seção obrigatória do modelo onde são declarados os componentes da AWS a serem criados (ex: `AWS::EC2::Instance`, `AWS::S3::Bucket`). |
| **Funções Intrínsecas** | Funções especiais (ex: `!Ref`, `!GetAtt`, `!Sub`, `!ImportValue`) usadas nos modelos para atribuir valores dinâmicos, referenciar outros recursos ou obter informações de *Outputs*. |
| **Parâmetros (Parameters)** | Seção opcional que permite definir valores de entrada personalizados para o modelo no momento da criação ou atualização da pilha. |
| **Saídas (Outputs)** | Seção opcional que permite exportar valores de recursos criados (ex: URL de um Load Balancer) para serem consumidos por outras pilhas. |
| **Change Sets** | Um resumo das alterações propostas em uma pilha em execução. Permite que você visualize como o CloudFormation modificará seus recursos antes de aplicar a mudança. |
| **Drift Detection** | Recurso que detecta se os recursos da pilha foram modificados manualmente (fora do CloudFormation) após o provisionamento, identificando desvios (`drift`) em relação ao modelo original. |
| **StackSets** | Extensão do CloudFormation que permite provisionar e gerenciar pilhas em **várias contas da AWS e/ou regiões** com uma única operação. |
| **AWS CDK** | Framework que permite definir a infraestrutura usando linguagens de programação de propósito geral (Python, TypeScript, etc.). O CDK transpila o código para modelos CloudFormation. |


### AWS CloudFormation: A Chave para a Infraestrutura como Código (IaC) Simples

O AWS CloudFormation é como um "engenheiro robótico" da AWS que constrói e gerencia sua infraestrutura na nuvem (servidores, bancos de dados, redes, etc.) de forma automatizada.

Em vez de clicar manualmente no console da AWS para criar um servidor e depois um banco de dados, você apenas escreve um **plano** do que quer, e o CloudFormation executa esse plano.

| Conceito Simplificado | Explicação em Linguagem Comum |
| :--- | :--- |
| **O que é (Em uma frase)?** | É um serviço que permite que você **descreva** sua infraestrutura da AWS em um arquivo de texto para que ela seja criada e gerenciada automaticamente. |
| **Infraestrutura como Código (IaC)** | É a prática de tratar sua infraestrutura (servidores, redes) como se fosse código de software. Isso significa que você pode **versionar, revisar e reutilizar** seu ambiente inteiro. |
| **Modelo (Template)** | Pense nisso como o **Plano de Construção** do seu ambiente. É um arquivo escrito em **YAML** ou **JSON** que lista todos os recursos da AWS que você precisa e como eles devem ser configurados. |
| **Pilha (Stack)** | É o **Resultado Final** do seu Plano de Construção. É o conjunto de todos os recursos da AWS que o CloudFormation criou com base no seu Modelo. Você gerencia todos eles como uma única unidade. |
| **Recursos (Resources)** | São os **Componentes** da AWS que você está construindo. Cada item na sua lista do Modelo é um Recurso (ex: um servidor EC2, um bucket S3). |
| **Parâmetros** | São as **Opções Personalizáveis** do seu plano. Permitem que você use o mesmo Modelo para criar ambientes diferentes (ex: usar o parâmetro "Ambiente" para escolher se a pilha será "Desenvolvimento" ou "Produção"). |
| **Saídas (Outputs)** | São as **Informações de Contato** dos seus novos recursos. Elas informam o endereço de acesso (URL) que o CloudFormation gerou, permitindo que outros ambientes o utilizem. |
| **Atualização** | Se você mudar algo no Plano, o CloudFormation descobre exatamente o que precisa ser alterado nos recursos existentes da sua Pilha, de forma segura. |
| **Exclusão** | Se você decidir que não precisa mais de um ambiente inteiro, basta deletar a Pilha. O CloudFormation remove **todos** os recursos que ele criou, sem deixar nada para trás. |

**Vantagens Chave**

* **Repetibilidade:** Crie ambientes idênticos (Produção, Teste, Desenvolvimento) de forma rápida e garantida, eliminando erros manuais.
* **Controle de Versão:** Seus planos (Modelos) são arquivos de código que podem ser armazenados no Git, permitindo rastrear o histórico de cada mudança na sua infraestrutura.
* **Gerenciamento Unificado:** Crie, atualize e exclua toda a sua infraestrutura com um único comando, tratando o ambiente inteiro como um bloco.