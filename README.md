# Microservices-HW4

## 4.1. Service endpoint design consideration
#### What is the main concepts and principles of Consumer Driven Contracts (CDC)?
CDC são basicamente contratos que especificam como as requisições e respostas de uma API devem ocorrer, agindo de forma similar ao TDD porém com enfoque em APIs.
Consumer-driven contracts possuem algumas características e propriedades, como ser fechado e completo em respeito a um conjunto de funcionalidades demandadas pelos consumidores, singular e não-autoritária pois é singular em termos de funcionalidades de negócios porém é não autoritária pois deriva da união das expectativas dos seus consumidores e por fim são estabilidade e imutabilidade sendo estável e imutável em respeito a um conjunto de consumidores, mas sujeito a mudanças de expectativas.
#### How does it fit into the microservices approach?
Devido a dificuldade de comunicação entre equipes diferentes desenvolvendo microserviços diferentes que devem fazer parte do mesmo sistema, prover um padrão que faça com que as próprias APIs falem por si só e sejam facilmente utilizadas por qualquer um é muito importante, logo ao estabelecer contratos, você permite que quem vá consumir a API saiba o mínimo para fazer as requisições e o mínimo que deve esperar ao fazer estas requisições.
#### How Postel's law could be also relevant in this scenario?
A lei de Postel diz que “temos que ser conservadores no que fazemos e liberal no que aceitamos dos outros”, desta forma não é aconselhável rejeitar requisições que estejam levemente fora dos padrões das requisições, ou seja, devemos flexibilizar a forma como aceitamos requisições, a fim de facilitar o uso da API pelos consumidores, onde uma estratégia simples, é apenas ignorar os campos extras que forem enviados pelo consumidor da API e trabalhando apenas com o que é necessário, uma vez que é muito difícil (praticamente impossível) flexibilizar a API para atender as necessidades de todos seus consumidores (que inclusive podem ser conflitantes).  
What are the main solutions (patterns, architectural styles, tools, etc.) to implement:
Message-oriented services;
HTTP and REST endpoints;
Optimized communication protocols;
API documentations.

O spring MVC oferece um grande suporte a implementação de CDC, com o spring cloud contract, através do wiremock e do stub runner, mas também existem outras ferramentas como o pact que é um conjunto de frameworks que dão suporte a testes de CDC dando suportando atualmente 9 linguagens de programação. Além destes também contamos com serviços de documentação de API como Swagger, serviços de mensageria como RabbitMQ, Kafka e Nats. Apis que provem endpoints de estado do seviço como Actuator. Além de uma série de APIs e bibliotecas providas pelo Spring Cloud.

## 4.2. Use of ESB and iPaaS with microservices
How can we have the same features present in EBS's with lightweight tools in the universe of microservices? Justify your answer.
Em um cenário em que é necessária uma comunicação heterogênea entre sistemas, normalmente cenários que envolvem sistemas novos e sistemas legados, o uso de um ESB é muito recomendado, porém em casos em que além deste cenário se quer adquirir características da arquitetura de microservices, como escalabilidade automática e seletiva, podemos utilizar a arquitetura de microservice. Porém para padronizar a comunicação, podemos usar o ESB como uma interface entre um conjunto de sistemas heterogêneos e os microservices, onde um gateway service direciona a integração entre os microservices e o barramento.

## 4.3. Microservices challenges - Data islands
How can be done data porting from microservices to a data lake or a data warehouse? Explain in details your answer.
Podemos enviar eventos aos microservices e quando esses eventos ocorrerem, ferramentas de ingestão de dados vão consumir  e propagar as mudanças no data lake apropriadamente.  Podemos usar ferramentas de ingestão de dados como kafka ou Spring Cloud Data Flow.



##### Referências
https://martinfowler.com/articles/consumerDrivenContracts.html
https://www.infoq.com/articles/consumer-driven-contracts
https://www.mulesoft.com/resources/esb/what-esb
https://www.bmc.com/blogs/data-lake-vs-data-warehouse-vs-database-whats-the-difference/
https://stackoverflow.com/questions/597397/what-is-an-esb-and-what-is-it-good-for
https://en.wikipedia.org/wiki/Robustness_principle
https://www.youtube.com/watch?v=IiK9A9nQ6NU
https://docs.pact.io/
https://cloud.spring.io/spring-cloud-contract/single/spring-cloud-contract.html
https://blogs.mulesoft.com/dev/microservices-dev/microservices-versus-esb/
