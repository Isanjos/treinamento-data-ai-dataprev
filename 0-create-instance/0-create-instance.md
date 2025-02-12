# Provisionar Serviços do OCI

## 📌 Introdução

>**A única nuvem que oferece serviços de nuvem completos em todo o mundo, entre nuvens ou em seu data center.** 
1. **Multicloud**
Faça várias nuvens funcionarem como uma. A Oracle oferece integração direta de banco de dados com o Microsoft Azure, bem como interconexão de alto desempenho.
2. **Nuvem Pública**
A única nuvem com um conjunto consolidado de serviços e preços baixos consistentes em regiões de nuvens públicas comerciais e governamentais.
3. **Nuvem Híbrida**
Soluções de nuvem confiáveis para praticamente qualquer local, incluindo Oracle Exadata Cloud@Customer, um banco de dados como serviço altamente otimizado já implementado em mais de 60 países.
4. **Nuvem Dedicada**
OCI Dedicated Region e Oracle Alloy são os únicos produtos que fornecem mais de 100 serviços a preços de nuvem pública inteiramente em seus data centers.
![Tipos de Nuvem](images/OCI.png)

### 📌 **Objetivos**

Demonstrar de forma prática como é fácil e ágil o provisionamento das soluções dentro do OCI.

O que você aprenderá:

- Criar um banco de dados autônomo (Autonomous Database) no Oracle Cloud Infrastructure (OCI);
- Provisionar Oracle Analytics Cloud, plataforma de autoatendimento de Análise de Negócio;
- Fazer a configuração do AI Agent.

<br>
### **Recursos e Suporte**:

- **Documentação da Oracle Cloud**: [Documentação do Oracle Cloud Infrastructure](https://docs.oracle.com/pt-br/iaas/Content/home.htm)
- **Introdução**: [Why Oracle Cloud Infrastructure](https://www.youtube.com/watch?v=ljiUqro6_Mc)


### _**Aproveite sua experiência na Oracle Cloud!**_


## 1️⃣ Validação de Região

1. Faça o login no Oracle Cloud Infrastructure (OCI) e valide se a região de Chicago se encontra disponível para uso.

   ![Validate Region](images/validate-region.png " ")

> **Caso a região de Chicago não esteja disponível, clique em manage region (caso já esteja disponível pule para a sessão 2 - Criação de Autonomous Database)** 
![Manage Region](images/manage-region.png)

2. Busque por **US Midwest (Chicago)** e clique no botão subscribe. O processo de subscrição pode levar alguns minutos, aguarde para dar sequência ao workshop. Clique no ícone escrito **Oracle Cloud** no canto esquerdo e faça logoff e login para validar se a região já foi subscrita.

![Subscribe Region](images/subscribe-region.png)

## 2️⃣ Criação de Autonomous Database

1. Clique no menu de hambúrger do canto superior esquerdo da tela, na sequência navegue até a página de gestão de autonomous databases.

![Autonomous Acess](images/autonomous-acess.png)

2. Na página de gestão de Autonomous Databases, clique em create autonomous database. Selecione **ATP ou ADW**
  
![Create Autonomous](images/create-autonomous.png)

3. Escolha a versão 23ai para o banco de dados:

![Create 23AI](images/create-23ai.png)

4. Coloque a senha **WORKSHOPsec2019##** , escolha **secure access from everywhere** e clique em **Create Autonomous Database**:
<br><br>

![Secure Acess](images/secure-acess.png)

5. Aguarde até a conclusão da criação: 
- Ícone amarelo = criando; 
- Ícone verde = pronto para uso;
![Yellow ADW](images/yellow-adw.png)
![Green ADW](images/green-adw.png)

## 3️⃣ Criação do Oracle Analytics Cloud

Clique no menu de hambúrger do canto superior esquerdo da tela, na sequência navegue até a página de gestão do Oracle Analytics Cloud.

![Analytics Cloud Acess](images/AcessoAnalytics.png)

Na página de gestão do Oracle Analytics Cloud, clique em **Create Instance**.
  
![Create Analytics Cloud](images/CreateOAC.png)

Dê um nome a instância do Analytics Cloud e mantenha as outras configurações como na imagem a seguir. Ao finalizar clique em **Create**:

![Configurando Analytics Cloud](images/CreateOAC1.png)
![Configurando Analytics Cloud](images/CreateOAC2.png)

Aguarde até a conclusão da criação: 
- Ícone amarelo = criando; 
- Ícone verde = pronto para uso;
![Green OAC](images/CreateOAC3.png)

Após a criação do OAC, você está pronto para prosseguir para o próximo laboratório.

## 4️⃣ Criação de Bucket no Object Storage e Upload de PDF

> **ATENÇÃO: Certifique-se de estar na região US Midwest (Chicago)**

Na guia do navegador com o OCI aberto, clique no menu de hambúrguer localizado no canto superior esquerdo da tela. Em seguida, selecione **Storage** e depois **Buckets**.

![Buckets](images/buckets.png)


Clique em **Create Buckets**. Em seguida, insira um nome para o seu bucket. Recomendamos o nome **ai-agent-buckets**. Finalize clicando em **Create**.

![Create Buckets](images/create-buckets.png)

![Name bucket](images/name-bucket.png)

Após a criação do bucket, clique em seu nome para acessá-lo. Em seguida, clique em **Upload**, selecione os arquivos PDFs desejados do seu computador, **clique e arraste para a região delimitada** e finalize clicando em **Upload** na parte inferior da tela.

Neste laboratório utilizaremos dois documentos:
- [Normas Internas Dataprev](https://www.dataprev.gov.br/governanca/normativos/normasinternas): Para o nosso exemplo, utilizaremos o arquivo **Viagem a Serviço Nacional**.
- [Revista Dataprev Resultados nº 16](https://www.dataprev.gov.br/acompanhe-dataprev-publicacoes/revista-dataprev-resultados): Para o nosso exemplo, utilizaremos o arquivo **Revista Dataprev Resultados nº 16**.

![Upload PDF](images/upload-pdf.png)

Aguarde a conclusão do processo. Em seguida, clique em **Close**. O arquivo deve aparecer em seu bucket como na imagem identificada abaixo.

![Close](images/close.png)
![Bucket PDF](images/bucket-pdf.png)

## 5️⃣ Criação da Base de Conhecimento (Knowledge Base)

Clique no menu de hambúrguer localizado no canto superior esquerdo da tela. Em seguida, selecione Analytics & AI e depois Generative AI Agents.

![Menu Agents](images/menu-agents.png)

Na página inicial do serviço, no menu à esquerda, selecione a opção **Knowledge Bases**.

![Knowledge Menu](images/knowledge-menu.png)

Selecione **Create Knowledge Base**, conforme indicado abaixo.

![Create Knowledge](images/create-knowledge.png)

Nesta tela, siga os passos abaixo:  
1. Insira o nome da sua base de conhecimento. Recomendamos utilizar **knowledge-base-agent**.  
2. No campo **Data Source Type**, selecione a opção **Object Storage**.  
3. Selecione a opção **Enable Hybrid Search**, que combina pesquisa semântica (busca baseada no significado e contexto) e pesquisa lexical (busca por correspondência exata de termos), garantindo resultados mais precisos e relevantes.
4. Clique em **Specify Data Source** para configurar os arquivos que serão utilizados pelo Agent.  

![Informations Knowledge](images/informations-knowledge.png)

Na tela seguinte, siga os passos abaixo:
1.  Insira o nome da sua fonte de dados. Recomendamos utilizar **pdfs-dataprev**
2.  Marque a opção **Enable Multi-Modal Parsing** para permitir a interpretação de gráficos, tabelas e outros elementos visuais dos documentos.
3.  Em Select bucket, escolha o bucket previamente criado (neste exemplo, bucket-ai-agent).
4.  Marque a caixa ao lado de **Object prefixes** para selecionar os arquivos que serão utilizados. Você poderá escolher entre 1 ou mais arquivos.
5.  Clique em **Create** para finalizar a criação da fonte de dados.

![Data Source](images/data-source.png)

Na tela de criação da base de conhecimento, marque a opção **Automatically start ingestion job for above data sources**. Em seguida, clique em **Create**.

![Creating Knowledge Base](images/creating-knowledge-base.png)

Verifique as mensagens no canto superior direito, indicando o sucesso na criação da base de conhecimento, da fonte de dados e do job de ingestão.

O status da base de conhecimento aparecerá como **Creating** até que o processo seja concluído, cuja média de tempo é de **3-5 minutos**. Aguarde a finalização antes de prosseguir.

![Sucess Messages](images/sucess-messages.png)

## 6️⃣ Criação do Agente de IA

No menu à esquerda, selecione a opção **Agents**. Em seguida, clique em **Create Agent**

![Agents](images/agents.png)

Nesta tela, siga os seguintes passos:
1. Insira o nome do agente. Recomendamos o nome **ai-agent**.
2. No campo **Welcome Message**, insira a mensagem de boas-vindas que será exibida para o usuário ao iniciar a interação com o agente. Exemplo: 
> **"Olá! Sou seu assistente virtual para documentos. Como posso ajudar você hoje?"**

3. No campo **Instructions for RAG Generation**, adicione instruções específicas para o agente. No exemplo, foi utilizado:  
> **"Você é um assistente virtual especialista em leitura de documentos. Responda sempre de forma clara e exclusivamente em português brasileiro."**

4. Na seção **Add Knowledge Bases**, selecione a base de conhecimento que será vinculada ao agente. Certifique-se de que a base de conhecimento está ativa. **O Lifecycle State deve aparecer como Active.**


![Configuration Agents](images/configuration-agents.png)

Certifique-se de que a opção **Automatically create an endpoint for this agent** está marcada. Isso permitirá que o sistema crie automaticamente um endpoint para o agente, facilitando a interação com ele via API com outras aplicações.

Clique no botão **Create** para finalizar a criação do agente.

![Create Agent](images/create-agent.png)


Nesta tela, aceite o Acordo de Licença e Política de Uso do Llama 3, o modelo de inteligência artificial utilizado pelo Agent.

![LLAMA3](images/llama3.png)

No canto superior direito, verifique as mensagens de confirmação. Elas devem indicar que a criação do agente  e do endpoint foram concluídas com sucesso.

O campo **Lifecycle State** exibirá o status como **Creating**, com média de tempo  de **3-5 minutos** para finalização. Aguarde até que o status mude para **Active**, indicando que o agente está pronto para uso.

![Sucess Messages Agent](images/sucess-messages-agent.png)

Clique no nome do agente e, em seguida, selecione a opção **Launch Chat** para iniciar a interação com o agente.

![Launch Chat](images/launch-chat.png)

> **ATENÇÃO: Caso o agente esteja ativo e o botão não esteja disponível, acesse o menu à esquerda inferior e selecione Endpoints. Verifique se o Lifecycle State do endpoint está como Active. Se o status estiver como Creating, aguarde a finalização e atualize a página.**
![Endpoints](images/endpoints.png)


## 👥 Agradecimentos

- **Autores** - Caio Oliveira
- **Autores Contribuintes** - Isabelle Anjos, Gabriela Miyazima, Aristotelles Serra
- **Última Atualização Por/Data** - Janeiro 2025

## 🛡️ Declaração de Porto Seguro (Safe Harbor)

O tutorial apresentado tem como objetivo traçar a orientação dos nossos produtos em geral. É destinado somente a fins informativos e não pode ser incorporado a um contrato. Ele não representa um compromisso de entrega de qualquer tipo de material, código ou funcionalidade e não deve ser considerado em decisões de compra. O desenvolvimento, a liberação, a data de disponibilidade e a precificação de quaisquer funcionalidades ou recursos descritos para produtos da Oracle estão sujeitos a mudanças e são de critério exclusivo da Oracle Corporation.

Esta é a tradução de uma apresentação em inglês preparada para a sede da Oracle nos Estados Unidos. A tradução é realizada como cortesia e não está isenta de erros. Os recursos e funcionalidades podem não estar disponíveis em todos os países e idiomas. Caso tenha dúvidas, entre em contato com o representante de vendas da Oracle. 
