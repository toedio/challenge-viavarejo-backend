# Desafio Backend
Eu sou o Victor candidato a vaga de desenvolvedor Java da Via Varejo.

Contatos: toedio6@gmail.com / 11 99656-6750

## Tecnologias
- Java 8
- Spring Boot 2.2.6
- Maven
- Redis
- Docker

## Decis�es T�cnicas

### Cache de aplica��o utilizando Redis
Eu implementei cache no servi�o de busca taxa de juros SELIC. Essa op��o melhora a performance da aplica��o evitando fazer a requisi��o na API externa todas as vezes que a consulta for feita. Foi utilizado como chave do cache a data, portanto ele zera o cache todos os dias evitando que o servi�o responda uma taxa de juros desatualizada. Utilizei o banco de dados Redis que � muito perform�tico e ideal para cache.

### Valida��es no Controller
A classe InstallmentController possui nota��es de valida��o como @Valid e @NotNull e os DTOS tamb�m possui dentro de seus m�todos. Eu escolhi fazer a valida��o na primeira camada porque dessa forma evita que a aplica��o processe objetos inv�lidos e responda o cliente imediatamente caso tenha objetos inv�lidos. Outra vantagem � que os servi�os j� recebem os objetos totalmente validados.

### Converters
A aplica��o tem um servi�o de convers�o de objetos utilizado para converter DTO em entidade e vice-versa e esse servi�o � utilizado na classe InstallmentController. Dessa forma, o servi�o conhece apenas as entidades e o controller apenas os DTOs.

### Docker Compose
A aplica��o utiliza a tecnologia docker compose que inicia automaticamente todas as depend�ncias e em seguida inicia a aplica��o na porta 8080. 
Eu escolhi essa tecnologia porque � uma ferramenta de f�cil utiliza��o para executar v�rios containers ao mesmo tempo, permite que a aplica��o execute em qualquer ambiente, tenha sua infraestrutura sempre padronizada evitando falhas por vers�o da JDK por exemplo.

## Servi�os
Foi criado apenas um servi�o conforme solicitado e o mesmo foi documentado bem como os DTOs utilizando swagger. A documenta��o fica dispon�vel assim que a API iniciar em http://localhost:8080/swagger-ui.html

## Executar os testes
Comando ```mvn test```

## Executar aplica��o
A aplica��o foi criada utilizando a estrutura de docker compose conforme falado acima. Quando executar o comando iniciar� o redis (necess�rio para o cache) e em seguida a aplica��o;

Comando ```docker-compose up```

Caso n�o tenha docker-compose instalado: https://docs.docker.com/compose/gettingstarted/
