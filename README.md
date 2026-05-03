---
title: Estudo e caracterização de aplicações de microsserviços de código aberto
class: Sistemas Distribuídos
professor: Nabor das Chagas Mendonça
authors:
  - Izabella Maria Pinheiro Amorim
  - Leticia Vasconcelos Machado
  - Leonardo de Freitas Rabelo
  - Renan Medeiros Aguiar
---

# Estudo e caracterização de aplicações de microsserviços de código aberto

## Introdução

Este trabalho tem como objetivo realizar uma análise comparativa de aplicações
de microsserviços de código aberto, com base em um conjunto de critérios
técnicos definidos. A proposta enfatiza a caracterização de sistemas reais a
partir de seus artefatos públicos, indo além de descrições e buscando evidências observáveis.

Para isso, foram selecionadas aplicações que apresentam diversidade em termos
de domínio, tecnologias utilizadas, estratégias de comunicação e níveis de
complexidade. A análise será conduzida segundo um protocolo comum, contemplando
aspectos como estrutura arquitetural, implementação, persistência de dados,
implantação e adequação para uso em ambientes de laboratório, especialmente em
cenários envolvendo conteinerização e orquestração com Kubernetes.

## Critério de Seleção das Aplicações

Inicialmente, foram considerados como pré-requisitos a existência de
repositório público acessível, a presença de documentação mínima de execução ou
implantação e a disponibilidade de artefatos como Dockerfiles, arquivos de
orquestração (Docker Compose ou Kubernetes), documentação arquitetural e
estrutura de código organizada. Esses elementos são fundamentais para
viabilizar a análise baseada em evidências observáveis.

Adicionalmente, foi adotado como critério central a identificação explícita ou
implícita de arquitetura de microsserviços. Para isso, foram analisados
aspectos como a decomposição do sistema em múltiplos serviços independentes, a
existência de comunicação entre serviços por meio de APIs ou mecanismos de
mensageria, a presença de componentes como gateways de API, e a separação de
responsabilidades entre os serviços.

Outro fator determinante no processo de seleção foi a disponibilidade de
artefatos suficientes para análise técnica aprofundada. Foram priorizados
projetos que disponibilizam não apenas código-fonte, mas também elementos
relacionados à implantação e operação, como manifestos de Kubernetes, scripts
de automação, configurações de ambiente e, quando possível, suporte a
observabilidade e monitoramento.

Além dos critérios técnicos, buscou-se deliberadamente compor um conjunto de
aplicações com diversidade significativa, evitando a seleção de sistemas
excessivamente semelhantes. Essa diversidade foi considerada em múltiplas
dimensões, incluindo: (i) domínio de aplicação, contemplando desde sistemas de
e-commerce até plataformas de backend e aplicações voltadas a benchmarking;
(ii) linguagens de programação e frameworks utilizados, de modo a incluir
ambientes heterogêneos; (iii) estratégias de comunicação entre serviços,
abrangendo abordagens síncronas, assíncronas e híbridas; e (iv) diferentes
níveis de maturidade e complexidade operacional, incluindo desde aplicações
educacionais até sistemas com características próximas de ambientes de
produção.

Por fim, também foi considerada a adequação das aplicações para uso em
atividades práticas futuras, especialmente no contexto de implantação em
ambientes conteinerizados e orquestrados. Nesse sentido, foram priorizados
sistemas que apresentassem suporte a Docker e Kubernetes, bem como indícios 
de facilidade de configuração e execução, ainda que com diferentes
níveis de complexidade. Essa escolha visa não apenas atender aos objetivos
imediatos da atividade, mas também contribuir para etapas posteriores da
disciplina, que envolvem experimentação prática e avaliação de desempenho e
resiliência.

Dessa forma, a seleção realizada busca equilibrar rigor técnico, diversidade e
aplicabilidade prática, fornecendo uma base consistente para a caracterização
comparativa proposta neste trabalho.

## Protocolo de Caracterização

A análise das aplicações selecionadas foi conduzida a partir de um protocolo de
caracterização técnica, com o objetivo de garantir consistência,
comparabilidade e rastreabilidade entre os sistemas avaliados. Esse protocolo
foi definido com base nas diretrizes estabelecidas no documento da atividade,
sendo adaptado para enfatizar uma abordagem analítica fundamentada em
evidências observáveis nos artefatos públicos das aplicações.

A primeira dimensão, denominada Identificação Geral, tem como objetivo
contextualizar cada aplicação analisada. Nessa etapa, são levantadas
informações como nome do projeto, domínio de aplicação, organização
responsável, finalidade aparente (por exemplo, aplicação educacional,
demonstração tecnológica ou sistema com perfil de produção) e status de
manutenção. Esses elementos fornecem uma base interpretativa importante para as
análises subsequentes, especialmente no que diz respeito à maturidade e à
intencionalidade do projeto.

A segunda dimensão, Estrutura Arquitetural, concentra-se na caracterização da
organização interna dos sistemas sob a perspectiva de microsserviços. São
analisados aspectos como o número de serviços identificáveis, a separação entre
frontend e backend, a presença de gateways de API, mecanismos de descoberta de
serviços, e as estratégias de comunicação adotadas. Também são investigadas a
natureza da comunicação (síncrona, assíncrona ou híbrida) e a utilização de
componentes intermediários, como filas, brokers de mensagens ou sistemas de
streaming. Essa dimensão é central para verificar, de forma objetiva, o grau de
aderência ao estilo arquitetural de microsserviços.

A terceira dimensão, Implementação, busca compreender como os serviços são
desenvolvidos e organizados do ponto de vista tecnológico. São considerados
fatores como linguagens de programação utilizadas, frameworks empregados,
heterogeneidade tecnológica entre os serviços e grau de padronização da
implementação. Adicionalmente, são analisados indícios de boas práticas de
engenharia de software, como a presença de testes automatizados, pipelines de
integração contínua e automação de build. Essa análise permite inferir o nível
de maturidade técnica e organizacional dos projetos.

A quarta dimensão, Dados e Persistência, investiga as estratégias adotadas para
armazenamento e gerenciamento de dados. São avaliadas as tecnologias de banco
de dados utilizadas, a existência de múltiplos mecanismos de persistência
(relacionais, NoSQL, caches, filas), e a presença de padrões arquiteturais
relevantes, como banco de dados por serviço ou compartilhamento de dados entre
serviços. Essa dimensão é particularmente relevante em arquiteturas de
microsserviços, dado o impacto direto das decisões de persistência na
escalabilidade, consistência e acoplamento do sistema.

A quinta dimensão, Implantação e Operação, analisa os artefatos e mecanismos
disponíveis para execução dos sistemas em ambientes reais ou simulados. São
considerados o suporte a contêineres (Docker), ferramentas de orquestração
(Docker Compose, Kubernetes), existência de manifestos de implantação, scripts
de automação e indícios de suporte à observabilidade, como integração com
ferramentas de monitoramento e logging. Essa dimensão também contempla uma
avaliação qualitativa da complexidade de implantação, com base na quantidade de
etapas necessárias e na clareza da documentação disponível.

Por fim, a sexta dimensão, Adequação para Uso em Atividades de Laboratório,
propõe uma análise crítica orientada ao contexto da disciplina. Nessa etapa,
são discutidos aspectos como a viabilidade de uso da aplicação em experimentos
com Kubernetes, potencial para testes de desempenho e resiliência, suporte à
observabilidade e complexidade operacional. Além disso, são identificadas
vantagens e limitações de cada sistema como objeto de estudo, considerando o
equilíbrio entre realismo e viabilidade prática em ambiente acadêmico.

Dessa forma, o protocolo de caracterização adotado fornece uma estrutura
sistemática e replicável para a análise comparativa das aplicações,
contribuindo para a construção de um entendimento aprofundado sobre a
diversidade e as implicações práticas das arquiteturas de microsserviços.

## Caracterização Individual das Aplicações

Nesta seção, são apresentadas as caracterizações individuais das aplicações
selecionadas, com base no protocolo definido anteriormente. A análise foi
conduzida a partir de evidências observáveis nos artefatos públicos de cada
projeto, incluindo repositórios de código, documentação técnica e arquivos de
configuração.

### Sock Shop

#### Identificação Geral

O Sock Shop é uma aplicação de demonstração desenvolvida pela Weaveworks, com o
objetivo de ilustrar boas práticas de arquitetura de microsserviços. Trata-se
de um sistema de e-commerce simulado, amplamente utilizado em contextos
educacionais e experimentais. O projeto possui repositório público e é
relativamente estável, ainda que não esteja em desenvolvimento ativo recente.

#### Estrutura Arquitetural

A aplicação é composta por múltiplos serviços independentes, incluindo
catálogo, carrinho, pedidos, usuários e frontend. Há separação clara entre
frontend e backend, além da presença de um gateway de entrada. A comunicação
entre serviços ocorre predominantemente via HTTP (REST), com uso complementar
de mensageria em alguns componentes. A arquitetura apresenta características
clássicas de microsserviços, com divisão clara de responsabilidades.

#### Implementação

O sistema apresenta heterogeneidade tecnológica, com serviços implementados em
diferentes linguagens (Java, Go, Node.js e Python). Essa diversidade evidencia
um ambiente típico de microsserviços. Há suporte a testes e automação de build,
embora não de forma uniforme entre todos os serviços.

#### Dados e Persistência

Cada serviço possui seu próprio mecanismo de persistência, incluindo bancos
NoSQL e armazenamento em memória. Essa abordagem reforça o princípio de banco
por serviço. Também há uso de cache em componentes específicos.

#### Implantação e Operação

O projeto oferece suporte completo a Docker, Docker Compose e Kubernetes.
Existem manifestos de implantação e integração com ferramentas de
monitoramento. A implantação é relativamente acessível para fins didáticos.

#### Adequação para Laboratório

Altamente adequado para testes de resiliência, observabilidade e falhas
controladas. Baixa a média complexidade operacional, sendo ideal para ambientes
educacionais.

### Google Online Boutique

#### Identificação Geral

A aplicação Google Online Boutique é um projeto oficial do Google Cloud,
desenvolvido como demonstração de arquitetura de microsserviços em ambientes
Kubernetes. Trata-se de um sistema de e-commerce moderno, com forte foco em
observabilidade e cloud-native.

#### Estrutura Arquitetural

O sistema é composto por diversos serviços especializados (checkout, pagamento,
recomendação, frontend, entre outros). A comunicação ocorre majoritariamente
via gRPC, com uso complementar de HTTP. A arquitetura inclui frontend separado,
múltiplos serviços backend e integração com ferramentas de observabilidade.

#### Implementação

Há alta heterogeneidade tecnológica, com serviços implementados em Go, Python,
JavaScript e C#. O projeto apresenta elevado grau de padronização, além de
pipelines de build e testes automatizados bem definidos.

#### Dados e Persistência

Utiliza múltiplos mecanismos de armazenamento, incluindo bancos relacionais e
serviços em memória. A separação de dados por serviço é parcialmente adotada.

#### Implantação e Operação

Possui suporte robusto a Kubernetes, com manifestos completos e documentação
detalhada. É projetado para execução em ambientes cloud-native, com suporte a
service mesh.

#### Adequação para Laboratório

Altamente adequado para estudos de Kubernetes, comunicação via gRPC e
observabilidade. Complexidade operacional moderada a alta.

### DeathStarBench

#### Identificação Geral

O DeathStarBench é um conjunto de aplicações de benchmark voltado à avaliação
de desempenho de arquiteturas de microsserviços. É amplamente utilizado em
pesquisas acadêmicas.

#### Estrutura Arquitetural

Inclui diferentes aplicações (rede social, sistema de reservas, mídia), cada
uma composta por dezenas de serviços. A comunicação entre serviços é variada,
incluindo RPC, HTTP e mensageria.

#### Implementação

Apresenta grande diversidade de linguagens e frameworks, refletindo cenários
realistas. Possui scripts de teste e carga, voltados à análise de desempenho.

#### Dados e Persistência

Utiliza múltiplos bancos de dados (SQL e NoSQL), além de sistemas de cache e
filas. Há evidência de arquitetura distribuída complexa.

#### Implantação e Operação

Suporte a Docker e Kubernetes, com foco em experimentação. Inclui ferramentas
para benchmarking e análise de latência.

#### Adequação para Laboratório

Extremamente adequado para testes de desempenho e escalabilidade. Alta
complexidade operacional, exigindo maior preparo técnico.

### Appwrite

#### Identificação Geral

O Appwrite é uma plataforma open source de Backend-as-a-Service, voltada ao
desenvolvimento rápido de aplicações.

#### Estrutura Arquitetural

Organizado em serviços independentes (autenticação, banco de dados, storage,
funções). A comunicação ocorre via APIs REST e eventos internos. Arquitetura
modular baseada em containers.

#### Implementação

Predominância de PHP e Node.js, com padronização significativa entre os
serviços. Possui automação de build e integração contínua.

#### Dados e Persistência

Utiliza banco de dados relacional, armazenamento de arquivos e sistemas
auxiliares. Há centralização parcial de dados.

#### Implantação e Operação

Suporte a Docker e fácil implantação local. Documentação clara e acessível.

#### Adequação para Laboratório

Adequado para estudos de backend moderno e APIs. Baixa complexidade
operacional.

### Medusa JS

#### Identificação Geral

O Medusa JS é uma plataforma de e-commerce headless, voltada para aplicações
modernas baseadas em API.

#### Estrutura Arquitetural

Arquitetura modular, com separação entre backend e frontend. Embora não seja
puramente baseado em microsserviços, permite decomposição em serviços
independentes.

#### Implementação

Desenvolvido em Node.js, com forte uso de plugins e extensões. Estrutura bem
organizada e moderna.

#### Dados e Persistência

Utiliza banco relacional, com possibilidade de integração com outros serviços.
Predominância de banco centralizado.

#### Implantação e Operação

Suporte a Docker e documentação adequada. Implantação relativamente simples.

#### Adequação para Laboratório

Adequado para análise arquitetural e evolução de sistemas. Baixa a média
complexidade.

## Comparação Consolidada

Com base na aplicação do protocolo de caracterização descrito na seção
anterior, apresenta-se a seguir uma visão comparativa das aplicações
analisadas. O objetivo desta seção é identificar padrões arquiteturais,
diferenças relevantes e implicações práticas para uso em ambientes de
laboratório e estudo de microsserviços.

### Tabela Comparativa

| Critério | Sock Shop | Online Boutique | DeathStarBench | Appwrite | Medusa JS |
| --- | --- | --- | --- | --- | --- |
| Domínio | E-commerce (demo) | E-commerce (cloud-native) | Benchmark (social, hotel) | Backend-as-a-Service | E-commerce headless |
| Objetivo | Educacional | Demonstração tecnológica | Pesquisa / performance | Produção real | Produção real |
| Nº de Serviços | Médio (~10) | Médio (~10) | Alto (dezenas) | Médio | Baixo a médio |
| Frontend separado | Sim | Sim | Sim | Parcial | Sim |
| Gateway/API | Sim | Sim | Parcial | Sim | Sim |
| Comunicação | REST + eventos | gRPC + HTTP | RPC + REST + filas | REST | REST |
| Tipo de comunicação | Híbrida | Híbrida | Híbrida | Síncrona | Síncrona |
| Mensageria | Sim | Limitada | Sim | Sim | Não evidente |
| Linguagens | Diversas | Diversas | Diversas | PHP/Node | Node.js |
| Heterogeneidade | Alta | Alta | Muito alta | Média | Baixa |
| Banco por serviço | Sim | Parcial | Sim | Parcial | Não |
| Docker | Sim | Sim | Sim | Sim | Sim |
| Kubernetes | Sim | Sim | Sim | Parcial | Limitado |
| Observabilidade | Sim | Forte | Forte | Moderada | Limitada |
| Complexidade | Baixa/Média | Média/Alta | Alta | Baixa | Baixa/Média |
| Adequação didática | Alta | Alta | Média | Alta | Média |

### Análise Comparativa

A análise comparativa evidencia, inicialmente, que todas as aplicações
selecionadas apresentam algum grau de aderência ao estilo arquitetural de
microsserviços, ainda que com diferentes níveis de maturidade, complexidade e
fidelidade aos princípios desse paradigma. Essa variação é, inclusive,
desejável, pois permite uma compreensão mais abrangente das múltiplas formas de
implementação de microsserviços na prática.

Um primeiro aspecto relevante diz respeito à estrutura arquitetural e
organização dos serviços. Aplicações como Sock Shop e Google Online Boutique
apresentam uma decomposição clara em serviços relativamente independentes, com
responsabilidades bem definidas e separação explícita entre frontend e backend.
Já o DeathStarBench se destaca pela complexidade significativamente maior, com
um número elevado de serviços e interações, refletindo cenários mais próximos
de sistemas distribuídos reais de grande escala. Por outro lado, Appwrite e
Medusa JS adotam abordagens mais centralizadas em alguns aspectos, o que indica
uma transição entre arquiteturas modulares e microsserviços plenamente
distribuídos.

No que se refere às estratégias de comunicação entre serviços, observa-se uma
diversidade importante. Enquanto Appwrite e Medusa JS utilizam
predominantemente comunicação síncrona via APIs REST, aplicações como Online
Boutique incorporam o uso de gRPC, evidenciando preocupações com desempenho e
eficiência na comunicação. O DeathStarBench, por sua vez, apresenta uma
abordagem híbrida mais complexa, combinando múltiplos mecanismos, incluindo
mensageria, o que o torna particularmente relevante para estudos de latência,
throughput e comportamento sob carga.

Outro ponto de destaque é a heterogeneidade tecnológica. Aplicações como Sock
Shop, Online Boutique e DeathStarBench utilizam múltiplas linguagens e
frameworks, o que está alinhado com um dos princípios fundamentais dos
microsserviços: a independência tecnológica entre serviços. Em contraste,
Medusa JS apresenta maior uniformidade tecnológica, o que simplifica sua
operação, mas reduz a diversidade arquitetural. O Appwrite ocupa uma posição
intermediária, com certa padronização, mas ainda baseado em serviços separados.

Em relação à gestão de dados e persistência, nota-se que nem todas as
aplicações seguem rigorosamente o princípio de banco de dados por serviço. Sock
Shop e DeathStarBench apresentam evidências mais claras dessa abordagem,
enquanto Appwrite e Medusa JS mantêm, em certa medida, estruturas de dados mais
centralizadas. Essa diferença tem implicações diretas na escalabilidade e no
acoplamento entre serviços, sendo um ponto relevante para análise crítica.

Do ponto de vista de implantação e operação, todas as aplicações oferecem
suporte a contêineres, com predominância do uso de Docker. No entanto, o
suporte a Kubernetes varia significativamente. Projetos como Online Boutique e
Sock Shop apresentam integração mais completa e documentada com ambientes
orquestrados, enquanto Medusa JS e Appwrite possuem suporte mais limitado ou
indireto. O DeathStarBench, embora tecnicamente robusto, apresenta maior
complexidade de implantação, o que pode representar uma barreira em ambientes
educacionais.

Por fim, ao considerar a adequação para uso em atividades de laboratório,
observa-se que não existe uma aplicação universalmente superior, mas sim
adequações específicas a diferentes objetivos. Sock Shop e Online Boutique se
destacam como excelentes opções para estudos introdutórios e intermediários,
especialmente em temas como observabilidade e resiliência. DeathStarBench é
mais adequado para experimentos avançados de desempenho, enquanto Appwrite
oferece uma alternativa interessante para exploração de APIs e backend moderno
com menor complexidade operacional. Medusa JS, por sua vez, é útil para
discussões sobre evolução arquitetural e transição de sistemas monolíticos para
microsserviços.

Em síntese, a comparação evidencia que a adoção de microsserviços não é
homogênea, variando conforme os objetivos do sistema, o contexto de uso e as
decisões de engenharia adotadas. Essa diversidade reforça a importância de uma
análise crítica baseada em evidências, conforme proposto neste trabalho , e
contribui para uma compreensão mais aprofundada das implicações práticas desse
estilo arquitetural.

## Discussão

A análise comparativa das aplicações selecionadas evidencia que, embora todas
sejam rotuladas ou concebidas sob o paradigma de microsserviços, há uma
significativa variação na forma como esse estilo arquitetural é efetivamente
implementado na prática. Essa heterogeneidade se manifesta tanto na estrutura
dos sistemas quanto nas decisões tecnológicas e operacionais adotadas,
reforçando a ideia de que microsserviços não constituem um modelo rígido, mas
sim um conjunto de princípios interpretáveis conforme o contexto de cada
projeto.

Um dos principais achados desta análise refere-se à diversidade dos sistemas
estudados, que abrange desde aplicações educacionais simplificadas, como o Sock
Shop, até ambientes altamente complexos e orientados à pesquisa, como o
DeathStarBench. Essa diversidade é particularmente relevante no contexto da
disciplina, pois permite observar diferentes níveis de maturidade arquitetural
e compreender como decisões de design impactam diretamente aspectos como
escalabilidade, acoplamento, observabilidade e facilidade de implantação.

No que diz respeito à representatividade das aplicações, observa-se que
projetos como Google Online Boutique e Appwrite apresentam características mais
próximas de ambientes de produção, incluindo maior preocupação com
padronização, documentação e integração com ecossistemas modernos de
desenvolvimento. Em contraste, aplicações como Sock Shop e DeathStarBench
possuem caráter mais didático ou experimental, sendo projetadas para demonstrar
conceitos específicos ou servir como base para avaliação de desempenho. Essa
distinção é importante, pois influencia diretamente a forma como essas
aplicações podem ser utilizadas em contextos acadêmicos e profissionais.

Outro ponto relevante diz respeito à aderência aos princípios de
microsserviços. Embora todas as aplicações apresentem algum nível de
decomposição em serviços, nem todas seguem rigorosamente princípios como
independência total de dados, isolamento completo de serviços ou comunicação
predominantemente assíncrona. Em particular, observa-se que algumas aplicações
mantêm certo grau de centralização, seja na persistência de dados ou na
organização da lógica de negócio, o que pode indicar compromissos entre pureza
arquitetural e viabilidade prática.

Do ponto de vista da utilidade como objeto de estudo, as aplicações analisadas
demonstram grande potencial para uso em atividades laboratoriais, especialmente
em temas como implantação em Kubernetes, observabilidade e testes de
resiliência. No entanto, essa utilidade varia conforme o nível de complexidade
de cada sistema. Aplicações mais simples, como Sock Shop e Appwrite, são mais
acessíveis para etapas iniciais de aprendizado, enquanto sistemas mais
complexos, como DeathStarBench, demandam maior preparo técnico e infraestrutura
mais robusta.

Nesse sentido, destaca-se também a existência de desafios práticos para adoção
em laboratório. Entre eles, podem ser citados: a complexidade de configuração
de ambientes distribuídos, a necessidade de conhecimento prévio em ferramentas
como Docker e Kubernetes, e a dificuldade de interpretar e adaptar artefatos de
implantação em projetos mais complexos. Além disso, a ausência ou limitação de
documentação em alguns casos pode dificultar a reprodução dos experimentos,
exigindo maior esforço por parte dos estudantes.

Por fim, observa-se que a análise baseada em artefatos públicos, conforme
proposto no enunciado , mostrou-se adequada para a caracterização técnica das
aplicações, permitindo identificar padrões arquiteturais e inferir decisões de
engenharia. No entanto, essa abordagem também apresenta limitações, uma vez que
nem todas as decisões de design estão explicitamente documentadas, exigindo
interpretações que devem ser realizadas com cautela.

Dessa forma, a discussão evidencia que a escolha de aplicações para estudo de
microsserviços deve considerar não apenas a aderência ao modelo arquitetural,
mas também fatores como complexidade, documentação e adequação ao contexto de
uso, especialmente em ambientes educacionais.

## Conclusão

Este trabalho teve como objetivo realizar uma caracterização técnica
comparativa de aplicações de microsserviços de código aberto, com base na
análise de seus artefatos públicos. A partir da aplicação de um protocolo
estruturado, foi possível identificar diferentes abordagens arquiteturais,
estratégias de implementação e níveis de maturidade entre os sistemas
analisados.

Os resultados obtidos indicam que, embora o conceito de microsserviços seja
amplamente adotado, sua implementação na prática varia significativamente,
refletindo diferentes objetivos, contextos e restrições de projeto. Essa
diversidade reforça a importância de uma análise crítica baseada em evidências,
permitindo compreender não apenas as vantagens, mas também os desafios
associados a esse estilo arquitetural.

Além disso, a análise evidenciou que algumas aplicações se destacam como mais
adequadas para uso em atividades práticas da disciplina. Em particular,
projetos como Sock Shop e Google Online Boutique apresentam um equilíbrio
favorável entre complexidade, documentação e aderência aos princípios de
microsserviços, sendo especialmente indicados para estudos envolvendo
implantação em Kubernetes, observabilidade e testes de resiliência. Por outro
lado, aplicações como DeathStarBench são mais indicadas para experimentos
avançados de desempenho, enquanto Appwrite e Medusa JS contribuem para a
compreensão de arquiteturas modernas em contextos próximos de produção.

No contexto da disciplina, os achados deste trabalho fornecem uma base sólida
para as etapas práticas subsequentes, permitindo uma escolha mais informada das
aplicações a serem utilizadas em experimentos de laboratório. Além disso, a
análise contribui para o desenvolvimento de uma visão crítica sobre o uso de
microsserviços, destacando a necessidade de avaliar cuidadosamente os
trade-offs envolvidos em sua adoção.

Por fim, conclui-se que o estudo de aplicações reais de código aberto constitui
uma estratégia eficaz para a compreensão de arquiteturas modernas de software,
especialmente quando conduzido de forma sistemática e baseada em evidências,
conforme proposto neste trabalho . Tal abordagem não apenas fortalece o
aprendizado teórico, mas também prepara os estudantes para os desafios práticos
encontrados em ambientes profissionais e de pesquisa.

## Referências

APPWRITE. Appwrite - Open-Source Backend Server. Disponível em: https://github.com/appwrite/appwrite. Acesso em: 28 abr. 2026.

APPWRITE. Documentation. Disponível em: https://appwrite.io/docs. Acesso em: 28 abr. 2026.

DEATHSTARBENCH. DeathStarBench: A Benchmark Suite for Microservices. Disponível em: https://github.com/delimitrou/DeathStarBench. Acesso em: 28 abr. 2026.

GOOGLE CLOUD. Online Boutique Microservices Demo. Disponível em: https://github.com/GoogleCloudPlatform/microservices-demo. Acesso em: 28 abr. 2026.

MEDUSA. Medusa: Open-Source Headless Commerce. Disponível em: https://github.com/medusajs/medusa. Acesso em: 28 abr. 2026.

MEDUSA. Documentation. Disponível em: https://docs.medusajs.com. Acesso em: 28 abr. 2026.

NEWMAN, Sam. Building Microservices: Designing Fine-Grained Systems. 2. ed. Sebastopol: O’Reilly Media, 2021.

WEAVEWORKS. Sock Shop Microservices Demo Application. Disponível em: https://github.com/microservices-demo/microservices-demo. Acesso em: 28 abr. 2026.

WEAVEWORKS. Sock Shop Documentation. Disponível em: https://microservices-demo.github.io. Acesso em: 28 abr. 2026.
