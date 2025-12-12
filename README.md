📅 API de Agendamentos (Laravel, Docker, Redis)

Este projeto é uma API RESTful para gerenciamento de agendamentos, desenvolvida com Laravel e conteinerizada utilizando Docker. O sistema utiliza Redis para cache e gerenciamento de filas (queues), e sua arquitetura é fundamentada nos princípios SOLID e no design pattern MVC.

🚀 Configuração e Instalação

O ambiente de desenvolvimento é totalmente gerenciado pelo Docker Compose, garantindo que todas as dependências (PHP, Servidor Web, Banco de Dados e Redis) sejam inicializadas corretamente.

    Clonar o Repositório: Obtenha o código-fonte.

    Configurar Variáveis: Crie e edite o arquivo .env para definir a chave da aplicação, as credenciais do banco de dados e as configurações do Redis.

    Iniciar o Ambiente: Utilize o Docker Compose para subir todos os contêineres necessários (Aplicação, Banco de Dados, Redis).

    Executar Migrações: As tabelas do banco de dados são criadas executando as migrações do Laravel dentro do contêiner da aplicação.

🛑 Observação sobre Redis

O Redis é configurado para ser o driver padrão tanto para Caching (melhorando a performance da leitura) quanto para Queues (permitindo o processamento assíncrono de tarefas como envio de e-mails de confirmação e notificações).

🏛️ Arquitetura e Padrões de Design

O código é estruturado para garantir alta coesão e baixo acoplamento, seguindo as melhores práticas do desenvolvimento moderno.
1. Princípios SOLID

    Responsabilidade Única (SRP): Os Controllers são mantidos "magros", lidando apenas com a requisição HTTP. A lógica de negócio é extraída para Service Classes dedicadas (CreateAppointmentService, CancelAppointmentService), assegurando que cada classe tenha apenas uma razão para mudar.

    Inversão de Dependência (DIP): Uso de Interfaces e do Container de Injeção de Dependência do Laravel para desacoplar componentes de alto nível (Serviços) de implementações de baixo nível (Repositórios de Dados).

2. Design Pattern MVC

    Model: Classes Eloquent que gerenciam a persistência dos dados e a lógica de negócio ligada diretamente ao recurso (ex: Appointment.php).

    Controller: Ponto de entrada das requisições, responsável por delegar tarefas e retornar a resposta formatada.

    View: Substituída por Resource Classes (Laravel API Resources) para padronizar e versionar a estrutura JSON das respostas.
