# Smart Home Energy Management API

## **Descrição**

A **Smart Home Energy Management API** é uma solução desenvolvida em **.NET Core 8** para ajudar no gerenciamento e otimização do consumo de energia em residências. A aplicação segue os princípios de arquitetura de software como **modularidade**, **escalabilidade**, e **separação de responsabilidades**, integrando tecnologias modernas, como **MongoDB** para armazenamento de dados e **OpenAI API** para previsão de padrões de consumo energético.


## **Grupo EcoTech**

### **Integrantes**:
- **Diego Mecco** - RM 98768
- **João Pedro Brito Deveza** - RM 551459
- **Marcos Henrique** - RM 98348
- **Vicenzo Guardabassi** - RM 550208
- **Luana Duque** - RM 550813



---

## **Recursos**

1. **Gerenciamento de Consumo de Energia**:
   - CRUD completo para registros de consumo.
   - Recuperação de registros por intervalo de datas.
   - Identificação de períodos de pico no consumo.

2. **Previsão com IA Generativa**:
   - Utiliza a **OpenAI API** para prever padrões de consumo com base em dados históricos.

3. **Documentação de API**:
   - Documentada com **Swagger** para facilitar o entendimento e o uso.

4. **Design Patterns**:
   - **Repository Pattern**: Implementado para gerenciar os dados de consumo.
   - **Factory Pattern**: Usado para criação dinâmica de objetos `Consumption`.

5. **Banco de Dados**:
   - Utiliza **MongoDB** como banco de dados NoSQL para armazenamento eficiente e flexível.

6. **Testes Automatizados**:
   - Desenvolvidos com **xUnit** e **Moq** para garantir a qualidade do código.

7. **Qualidade de Código**:
   - Configurado com **Roslyn Analyzers** e **.editorconfig** para manter boas práticas de desenvolvimento.

---

## **Tecnologias Utilizadas**

- **.NET Core 8**
- **MongoDB**
- **Swagger**
- **OpenAI API**
- **xUnit e Moq**
- **Roslyn Analyzers**
- **Logger do .NET**

---

## **Configuração e Execução**

### **Pré-requisitos**

1. **.NET 8 SDK** instalado.
2. **MongoDB** rodando localmente ou em um servidor configurado.
3. **Chave da OpenAI API** para funcionalidades de IA.

### **Configuração do Projeto**

1. Clone o repositório:
   bash
   git clone https://github.com/jpdeveza/smart-home-energy-management-api.git
   cd smart-home-energy-management-api


   2. Configure o arquivo appsettings.json:

Certifique-se de que as conexões e chaves estão corretas:

{
  "ConnectionStrings": {
    "MongoDB": "mongodb://localhost:27017/EnergyManagement"
  },
  "OpenAI": {
    "ApiKey": "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",
    "BaseUrl": "https://api.openai.com/v1"
  },
  "EnergySettings": {
    "PeakConsumptionThreshold": 50.0
  }
}


3. Restaure as dependências:

dotnet restore


4.Execute o projeto:

dotnet run 



Testando a API

1.Acesse o Swagger:
URL local: http://localhost:5000/swagger

2.Teste endpoints diretamente no Swagger ou via Postman.

Principais Endpoints
Consumo
GET /api/consumption: Recupera todos os registros de consumo.
GET /api/consumption/{id}: Recupera um registro pelo ID.
GET /api/consumption/daterange?start={start}&end={end}: Recupera registros por intervalo de datas.
POST /api/consumption: Adiciona um novo registro.
PUT /api/consumption/{id}: Atualiza um registro.
DELETE /api/consumption/{id}: Exclui um registro.
IA Generativa
GET /api/consumption/predict-pattern?historicalData={data}: Gera uma previsão de padrões de consumo com base em dados históricos.
Factory Pattern
POST /api/consumption/create-from-factory?deviceId={deviceId}&kilowattHours={value}: Cria um objeto de consumo usando o padrão Factory.


Design Patterns Implementados
Repository Pattern:

Centraliza a lógica de acesso a dados.
Permite alternar entre diferentes fontes de dados com facilidade.
Factory Pattern:

Cria objetos Consumption dinamicamente com base no contexto.
Exemplo de uso no endpoint /api/consumption/create-from-factory.




Estrutura do Projeto

SmartHomeEnergyAPI/
?
??? Controllers/
?   ??? ConsumptionController.cs        # Controlador principal para consumo
?
??? Models/
?   ??? Consumption.cs                  # Modelo de dados de consumo
?
??? Services/
?   ??? IConsumptionService.cs          # Interface para o serviço de consumo
?   ??? ConsumptionService.cs           # Implementação do serviço
?   ??? IAIService.cs                   # Interface para IA
?   ??? AIService.cs                    # Implementação do serviço de IA
?
??? Factories/
?   ??? IConsumptionFactory.cs          # Interface para Factory
?   ??? ConsumptionFactory.cs           # Implementação da Factory
?
??? Repositories/
?   ??? IConsumptionRepository.cs       # Interface para Repositório
?   ??? ConsumptionRepository.cs        # Implementação do Repositório
?
??? Infrastructure/
?   ??? MongoDBContext.cs               # Configuração do MongoDB
?
??? appsettings.json                    # Configurações do projeto
??? Program.cs                          # Ponto de entrada da aplicação




Testes Automatizados

Os testes foram implementados usando xUnit e Moq.
Principais cenários cobertos:
Validação de operações do ConsumptionService.
Criação de objetos usando a ConsumptionFactory.



Para rodar os testes:

bash
dotnet test
