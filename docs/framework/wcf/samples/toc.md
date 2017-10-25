# [Windows Communication Foundation Samples](index.md) (Amostras do Windows Communication Foundation)
## [Instruções de configuração](set-up-instructions.md)
### [Procedimento de configuração única para os exemplos do Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md)
#### [Instruções do firewall](firewall-instructions.md)
#### [Hospedagem instruções de serviço de informações da Internet](internet-information-service-hosting-instructions.md)
#### [Serviços de informações da Internet (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md)
#### [Instruções de configuração do diretório virtual](virtual-directory-setup-instructions.md)
#### [Instalando o enfileiramento de mensagens (MSMQ)](installing-message-queuing-msmq.md)
### [Compilando os exemplos do Windows Communication Foundation](building-the-samples.md)
### [Executando os exemplos do Windows Communication Foundation](running-the-samples.md)
## [Básico](basic.md)
### [Introdução](getting-started-sample.md)
### [AJAX](ajax.md)
#### [JSONP](jsonp.md)
#### [Serialização JSON](json-serialization.md)
#### [Serviço AJAX básico](basic-ajax-service.md)
#### [Serviço de AJAX utilizando o HTTP POST](ajax-service-using-http-post.md)
#### [Serviço AJAX sem configuração](ajax-service-without-configuration.md)
#### [Serviço de AJAX utilizando tipos complexos](ajax-service-using-complex-types-sample.md)
#### [Serviço de AJAX com JSON e XML](ajax-service-with-json-and-xml-sample.md)
### [Associação](binding.md)
#### [Codificador ByteStream](bytestream-encoder.md)
#### [Associações básicas](basic-binding.md)
##### [Exemplo de segurança de mensagem](message-security-sample.md)
##### [BasicBinding com segurança de transporte](basicbinding-with-transport-security.md)
##### [BasicBinding](basicbinding.md)
#### [Associação personalizada](custom-binding.md)
##### [Associação personalizada obrigatória](custom-binding-imperative.md)
##### [Codificação e transporte de associação personalizado](custom-binding-transport-and-encoding.md)
##### [Sessão confiável de associação personalizada](custom-binding-reliable-session.md)
##### [Sessão confiável de associação via HTTPS personalizada](custom-binding-reliable-session-over-https.md)
##### [Segurança de associação personalizada](custom-binding-security.md)
#### [Associação de rede](net-binding.md)
##### [Associação de MSMQ de rede](net-msmq-binding.md)
###### [Associação transacionada do MSMQ](transacted-msmq-binding.md)
###### [Comunicação em fila volátil](volatile-queued-communication.md)
###### [Filas de mensagens mortas](dead-letter-queues.md)
###### [Tratamento no MSMQ 4.0 de mensagens suspeitas](poison-message-handling-in-msmq-4-0.md)
###### [Sessões e filas](sessions-and-queues.md)
###### [Comunicação bidirecional](two-way-communication.md)
###### [Envio em lote transacionado](transacted-batching.md)
###### [SRMP](srmp.md)
###### [Segurança no serviço de enfileiramento de mensagens](message-security-over-message-queuing.md)
###### [Gerador de produto de ReceiveContext](receivecontext-enabled-wcf-channels.md)
##### [Integração de enfileiramento de mensagens](message-queueing-integration.md)
###### [Enfileiramento de mensagens para o Windows Communication Foundation](message-queuing-to-wcf.md)
###### [Demux personalizado](custom-demux.md)
###### [O Windows Communication Foundation para enfileiramento de mensagens](wcf-to-message-queuing.md)
###### [Correlação de mensagem](message-correlation.md)
##### [NetTCPBinding](nettcpbinding.md)
###### [NetTcpBinding padrão](default-nettcpbinding.md)
###### [Exemplo de compartilhamento de porta NET. TCP](net-tcp-port-sharing-sample.md)
##### [NetNamedPipeBinding](netnamedpipebinding.md)
#### [Associação de WS](ws-binding.md)
##### [Associação de HTTP de Federação do WS 2007](ws-2007-federation-http-binding.md)
##### [Dual WS Http](ws-dual-http.md)
##### [Codificação de MTOM](mtom-encoding.md)
##### [WSHttpBinding](wshttpbinding.md)
##### [Sessão confiável de WS](ws-reliable-session.md)
##### [Segurança de transporte WS](ws-transport-security.md)
##### [Associação de segurança de mensagem](message-security-binding.md)
###### [Segurança de mensagem anônima](message-security-anonymous.md)
###### [Certificado de segurança de mensagem](message-security-certificate.md)
###### [Nome de usuário de segurança de mensagem](message-security-user-name.md)
###### [Janelas de segurança de mensagens](message-security-windows.md)
##### [Transporte de WS com credencial de mensagem](ws-transport-with-message-credential.md)
##### [Fluxo de transação WS](ws-transaction-flow.md)
### [Cliente](client.md)
#### [Interoperabilidade do cliente](client-interoperability.md)
##### [Interoperando com serviços Web ASMX](interoperating-with-asmx-web-services.md)
##### [Exemplo de XMLSerializer](xmlserializer-sample.md)
#### [Cabeçalhos de endereço](address-headers.md)
#### [Fábrica de canais](channel-factory.md)
#### [Exceções esperadas](expected-exceptions.md)
#### [Recuperar metadados](retrieve-metadata.md)
#### [Evitando problemas com a instrução Using](avoiding-problems-with-the-using-statement.md)
#### [Cliente tipado](typed-client.md)
### [Contrato](contract.md)
#### [Contratos de dados](data-contracts.md)
##### [Contrato de dados básicos](basic-data-contract.md)
##### [Exemplo de DataContractSerializer](datacontractserializer-sample.md)
##### [Tipos conhecidos](known-types.md)
##### [Referências de objeto](object-references.md)
##### [POCO suporte](poco-support.md)
##### [Uso do associador de serialização](usage-of-serialization-binder.md)
#### [Contratos de mensagem](message-contracts.md)
##### [Contrato de mensagem padrão](default-message-contract.md)
##### [Sem tipo de solicitação/resposta](untyped-request-reply.md)
##### [Mensagens sem](unwrapped-messages.md)
##### [Definindo as propriedades de estilo e uso](setting-the-use-and-style-properties.md)
##### [Exemplo de XmlReader](xmlreader-sample.md)
#### [Contratos de serviço](service-contracts.md)
##### [Duplex](duplex.md)
##### [Contrato de falha](fault-contract.md)
##### [Unidirecional](one-way.md)
##### [Sessão](session.md)
##### [Fluxo](stream.md)
##### [Falhas de XmlSerializer](xmlserializer-faults.md)
#### [DataContractResolver](datacontractresolver.md)
#### [KnownAssemblyAttribute](knownassemblyattribute.md)
#### [Usando o DataContractSerializer e DataContractResolver para fornecer a funcionalidade NetDataContractSerializer](datacontractserializer-datacontractresolver-netdatacontractserializer.md)
### [Descoberta](discovery-samples.md)
#### [Anúncios](announcements-sample.md)
#### [Assíncrono encontrado](asynchronous-find-sample.md)
#### [Básico](basic-sample.md)
#### [Configuração](configuration-sample.md)
#### [Amostra do elemento de associação de descoberta](discovery-binding-element-sample.md)
#### [Exemplo de Proxy de descoberta](discovery-proxy-sample.md)
#### [Descobrir um serviço com exemplo de modo de Uri de escuta exclusivo](discover-a-service-with-unique-listen-uri-mode-sample.md)
#### [Descoberta com escopos](discovery-with-scopes-sample.md)
#### [Critérios de localização personalizados](custom-find-criteria.md)
#### [Exemplo de descoberta de fluxo de trabalho](workflow-discovery-sample.md)
#### [Serviço de roteador de descoberta](discovery-router-service.md)
### [Gerenciamento](management.md)
#### [Serviços WCF e rastreamento de eventos do Windows](wcf-services-and-event-tracing-for-windows.md)
#### [Rastreamento analítico do WCF](wcf-analytic-tracing.md)
#### [Rastreamento circular](circular-tracing.md)
#### [Rastreamento ETW](etw-tracing.md)
#### [Estendendo rastreamento](extending-tracing.md)
#### [Bloqueio de segurança PII](pii-security-lockdown.md)
#### [Usando contadores de desempenho](using-performance-counters.md)
#### [Rastreamento e o registro de mensagem](tracing-and-message-logging.md)
#### [Validação de segurança](security-validation.md)
#### [Provedor WMI](wmi-provider.md)
### [Serviços de roteamento](routing-services.md)
#### [Hello World com o serviço de roteamento](hello-world-with-the-routing-service.md)
#### [Ponte e o tratamento de erros](bridging-and-error-handling.md)
#### [Filtros avançados](advanced-filters.md)
#### [Reconfiguração dinâmica](dynamic-reconfiguration.md)
#### [Tratamento avançado de erros](advanced-error-handling.md)
### [Segurança](security-in-wcf.md)
#### [Agilidade criptográfica de segurança do WCF](cryptographic-agility-in-wcf-security.md)
### [Serviços](services.md)
#### [Hospedagem](hosting.md)
##### [Ativação de processos do Windows](windows-process-activation.md)
###### [Ativação de pipe nomeado](namedpipe-activation.md)
###### [Ativação TCP](tcp-activation.md)
###### [Ativação de MSMQ](msmq-activation.md)
##### [Ativação baseada em configuração](configuration-based-activation.md)
##### [Integração de Systemwebrouting](systemwebrouting-integration-sample.md)
##### [Compatibilidade com ASP.NET](aspnet-compatibility.md)
##### [Hospedagem do IIS utilizando código embutido](iis-hosting-using-inline-code.md)
##### [Host de serviço do Windows](windows-service-host.md)
##### [Hospedagem interna](self-host.md)
#### [Interoperabilidade de serviço](service-interoperability.md)
##### [Usando o WCF Moniker com clientes COM](using-the-wcf-moniker-with-com-clients.md)
##### [Cliente ASMX com um serviço WCF](asmx-client-with-a-wcf-service.md)
#### [Comportamentos](behaviors.md)
##### [Simultaneidade](concurrency.md)
##### [Comportamento de serviço padrão](default-service-behavior.md)
##### [Criação de instância](instancing.md)
##### [Comportamento de publicação de metadados](metadata-publishing-behavior.md)
##### [Comportamento de transação de serviço](service-transaction-behavior.md)
##### [Comportamento de depuração de serviço](service-debug-behavior.md)
##### [Limitação](throttling.md)
##### [Segurança de comportamento](behavior-security.md)
###### [Comportamento de auditoria de serviço](service-auditing-behavior.md)
###### [Provedor de função e associação](membership-and-role-provider.md)
###### [Autorizando o acesso a operações de serviço](authorizing-access-to-service-operations.md)
###### [Representar o cliente](impersonating-the-client.md)
#### [Configuração simplificada para serviços WCF](simplified-configuration-for-wcf-services.md)
#### [Uso de pontos de extremidade padrão](usage-of-standard-endpoints.md)
#### [Modelo de configuração hierárquica](hierarchical-configuration-model.md)
#### [Política de proteção estendida](extended-protection-policy.md)
#### [Fábrica de canais de configuração](configuration-channel-factory.md)
#### [Endereçamento](addressing.md)
#### [Obrigatória](imperative.md)
#### [Vários contratos](multiple-contracts.md)
#### [Vários pontos de extremidade](multiple-endpoints.md)
#### [Vários pontos de extremidade em único ListenUri](multiple-endpoints-at-a-single-listenuri.md)
#### [OperationContextScope](operationcontextscope.md)
#### [Descrição do serviço](service-description.md)
#### [Reentrant](concurrencymode-reentrant.md)
#### [Segurança do serviço](service-security.md)
##### [Exemplo de identidade de serviço](service-identity-sample.md)
### [Distribuição](syndication.md)
#### [Feed de diagnóstico independente](stand-alone-diagnostics-feed-sample.md)
#### [Extensões tipadas vagamente](loosely-typed-extensions-sample.md)
### [Web](web.md)
#### [Seleção de formato avançada](advanced-format-selection.md)
#### [Seleção automática de formato](automatic-format-selection.md)
#### [Serviço básico de HTTP](basic-http-service.md)
#### [Serviço de recursos básicos](basic-resource-service.md)
#### [AspNetRouteIntegration](aspnetrouteintegration.md)
#### [Colocação e obtenção condicional](conditional-get-and-put.md)
#### [SOAP e pontos de extremidade HTTP](soap-and-http-endpoints.md)
#### [Integração de cache ASP.NET](aspnet-caching-integration.md)
#### [UriTemplate](uritemplate-sample.md)
#### [Tabela de UriTemplate](uritemplate-table-sample.md)
#### [Tabela de UriTemplate Dispatcher](uritemplate-table-dispatcher-sample.md)
## [Extensibilidade](extensibility.md)
### [Extensibilidade de associação](binding-extensibility.md)
#### [WSStreamedHttpBinding](wsstreamedhttpbinding.md)
### [Extensibilidade de canais](channels-extensibility.md)
#### [Canal local](local-channel.md)
#### [Perfil seguro confiável](reliable-secure-profile.md)
#### [Distribuidor de canal personalizado](custom-channel-dispatcher.md)
#### [Canal de agrupamento](chunking-channel.md)
#### [Canal de reconhecimento de HTTP](http-acknowledgement-channel.md)
#### [HttpCookieSession](httpcookiesession.md)
#### [Interceptor de mensagem personalizado](custom-message-interceptor.md)
### [Extensibilidade de descoberta](discovery-extensibility.md)
#### [CustomDiscoveryMetadata](customdiscoverymetadata.md)
### [Extensibilidade de instanciação](instancing-extensibility.md)
#### [Contexto de instância durável](durable-instance-context.md)
#### [Tempo de vida personalizado](custom-lifetime.md)
#### [Inicialização de instancialização](instancing-initialization.md)
#### [O pool](pooling.md)
### [Extensibilidade de interoperabilidade](interop-extensibility.md)
#### [Expedição por elemento Body](dispatch-by-body-element.md)
#### [Rota por corpo](route-by-body.md)
### [Extensibilidade de codificador de mensagem](message-encoder-extensibility.md)
#### [Codificador de mensagem personalizado: Codificador de texto personalizado](custom-message-encoder-custom-text-encoder.md)
#### [Codificador de mensagem personalizado: Codificador de compactação](custom-message-encoder-compression-encoder.md)
### [Extensibilidade de metadados](metadata-extensibility.md)
#### [Ponto de extremidade de metadados seguros personalizados](custom-secure-metadata-endpoint.md)
#### [Publicação de WSDL personalizado](custom-wsdl-publication.md)
### [Extensibilidade de segurança](security-extensibility.md)
#### [Provedor de Token emitido durável](durable-issued-token-provider.md)
#### [Provedor de Token SAML](saml-token-provider.md)
#### [Os Tokens de suporte](supporting-tokens.md)
#### [Autenticador de token](token-authenticator.md)
#### [Provedor de token](token-provider.md)
#### [Validador de senha do nome de usuário](user-name-password-validator.md)
#### [Validador de certificado x. 509](x-509-certificate-validator.md)
#### [Política de autorização](authorization-policy.md)
#### [Token personalizado](custom-token.md)
#### [Validação do cliente](client-validation.md)
### [Exemplos de extensibilidade de sindicalização](syndication-extensibility-samples.md)
#### [Extensões fortemente tipadas](strongly-typed-extensions-sample.md)
#### [Formatador do feed (JSON)](feed-formatter-json.md)
#### [Streaming Feeds](streaming-feeds-sample.md)
### [Extensibilidade de transporte](transport-extensibility.md)
#### [Ativação de UDP](udp-activation.md)
#### [Transporte: Transações personalizadas através de UDP](transport-custom-transactions-over-udp-sample.md)
#### [Transporte: UDP](transport-udp.md)
#### [Transporte: WSE 3.0 TCP interoperabilidade](transport-wse-3-0-tcp-interoperability.md)
### [Extensibilidade de Web](web-extensibility.md)
#### [Postagem de formulário](form-post.md)
### [Formatador de operação e seletor de operação](operation-formatter-and-operation-selector.md)
### [Filtro de mensagem personalizado](custom-message-filter.md)
### [Host de serviço personalizado](custom-service-host.md)
### [Alternativa de DataContract](datacontract-surrogate.md)
### [Estendendo o controle sobre o tratamento de erros e emissão de relatórios](extending-control-over-error-handling-and-reporting.md)
### [Inspetores de mensagem](message-inspectors.md)
### [WebContentTypeMapper](webcontenttypemapper-sample.md)
## [Cenário](scenario.md)
### [Cenários de associação de dados](data-binding-scenarios.md)
#### [Cliente de formulários de associação de dados em um Windows](data-binding-in-a-windows-forms-client.md)
#### [Associação de dados em um cliente do ASP.NET](data-binding-in-an-aspnet-client.md)
#### [Associação de dados em um cliente do Windows Presentation Foundation](data-binding-in-a-wpf-client.md)
### [Exemplo de segurança de descoberta](discovery-security-sample.md)
### [Exemplo de Federação](federation-sample.md)
### [Serialização JSON tipo fraco (AJAX)](weakly-typed-json-serialization-sample.md)
### [Serviço de fachada confiável](trusted-facade-service.md)
### [Padrões de design: Lista de publicação-assinatura baseada](design-patterns-list-based-publish-subscribe.md)
## [Exemplos de ferramentas](tool-samples.md)
### [ConfigurationCodeGenerator](configurationcodegenerator.md)
### [CustomChannelsTester](customchannelstester.md)
### [FindPrivateKey](findprivatekey.md)