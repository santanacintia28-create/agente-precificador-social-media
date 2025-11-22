# agente-precificador-social-media

Agente responsável por organizar trabalhos de social media e calcular valores com base em uma tabela de preços previamente cadastrada, retornando sempre resultados estruturados em JSON para uso em automações.

---

## 🧠 O que este agente faz

Um agente que recebe dois dados vindos de um formulário — **nome do cliente** e **tipo de trabalho** — cruza essas informações com uma tabela de preços pré-definida e retorna um JSON padronizado contendo:

- nome do cliente  
- tipo de trabalho  
- valor do trabalho  
- data de registro  

O objetivo é automatizar o fluxo de organização e precificação de jobs de social media, alimentando painéis, planilhas ou relatórios.

---

## 🎯 Objetivo do Agente

- Automatizar a organização de trabalhos por cliente e tipo de job;  
- Aplicar a precificação correta seguindo uma tabela de preços real;  
- Registrar tudo em uma planilha ou sistema para controle financeiro e operacional;  
- Facilitar a gestão e o fluxo de trabalho de social media.

---

## 📥 Entradas do Sistema

### Do Formulário (Forms):
- `nome_cliente`  
- `tipo_trabalho` (ex.: post estático, carrossel, vídeo curto, pacote mensal)

### Da tabela de preços vinculada ao agente:
- `tipo_trabalho`  
- `preco_base`  
- (opcional) observações, prazos etc.

---

## 📤 Saída Esperada (JSON)

```json
{
  "nome_cliente": "",
  "tipo_trabalho": "",
  "valor_trabalho": "",
  "data_registro": ""
}
Se o tipo de trabalho não existir na tabela:
{
  "erro": true,
  "mensagem": "Tipo de trabalho não encontrado na tabela de preços."
}
🔁 Arquitetura / Fluxo Lógico

A cliente preenche o Forms

O Forms dispara um fluxo (ex.: Power Automate)

O fluxo envia para o agente:

nome_cliente

tipo_trabalho

O agente executa a ação funcional CalcularPrecoEOrganizarJob

Ele consulta a tabela de preços associada

Ele retorna um JSON estruturado

O fluxo recebe o JSON

O fluxo adiciona uma nova linha na planilha Controle_Jobs_SocialMedia

⚙️ Ação Funcional do Agente: CalcularPrecoEOrganizarJob
Entrada:

nome_cliente (string)

tipo_trabalho (string)

Processo:

Verifica o tipo de trabalho na tabela de preços

Se existir, cria o JSON completo

Se não existir, retorna erro padronizado

Saída:
{
  "nome_cliente": "João Silva",
  "tipo_trabalho": "carrossel",
  "valor_trabalho": 180.00,
  "data_registro": "2025-11-22"
}

💬 Prompt interno do agente (Foundry)

Você é um agente especializado em organizar trabalhos de social media e precificar cada job com base em uma tabela de preços previamente cadastrada.

Suas funções principais incluem:

Receber o nome do cliente e o tipo de trabalho;

Consultar exclusivamente a tabela de preços associada ao agente;

Retornar JSON estruturado contendo nome_cliente, tipo_trabalho, valor_trabalho, data_registro;

Se o tipo não existir, retornar JSON de erro;

Nunca inventar valores ou tipos novos.

Mantenha as respostas objetivas e adequadas para uso em automação.

🖼 Prints (adicione os seus depois)

Crie uma pasta chamada prints e depois coloque seus prints lá.

![print do agente](./prints/agente.png)
![fluxo funcionando](./prints/fluxo.png)
![JSON retornado](./prints/json.png)

🔗 Referências

Microsoft Foundry

Microsoft Power Automate

GitHub
