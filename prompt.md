Claude terminou a resposta
Prompt para o Claude Code
Atue como um Engenheiro de Software Full-Stack Sênior. Sua tarefa é inicializar e desenvolver uma aplicação completa de Calculadora com Histórico Persistente. Você deve criar a estrutura de pastas, os arquivos de configuração e todo o código-fonte necessário.
 ESPECIFICAÇÕES GERAIS E STACK

Frontend: React, Vite e TypeScript.
Backend: C# com .NET (Web API).
Banco de Dados: PostgreSQL rodando em Docker.
Conceito: Uma calculadora no estilo "Calculadora do Windows", com painel de histórico.
ARQUITETURA E REGRAS DE NEGÓCIO OBRIGATÓRIAS (CRÍTICO)

Zero cálculos no Frontend: O frontend é apenas uma interface "burra". Ele deve enviar os operandos (números) e o operador (+, -, *, /) para o backend. O frontend NÃO PODE usar eval() ou fazer a matemática em JavaScript/TypeScript.
Cálculo no Backend: A API em C# deve receber a requisição, realizar a operação matemática, salvar no banco de dados e retornar o resultado para o frontend.
Persistência: TODO cálculo bem-sucedido deve ser salvo no PostgreSQL. A tabela deve armazenar: Expressão completa (ex: "5 + 5"), Resultado ("10") e Data/Hora (Timestamp).
 DETALHES DO FRONTEND (React + Vite + TS)

Crie o projeto dentro de uma pasta chamada calculadora-frontend.
Interface e Estética: O design deve ser um clone da Calculadora do Windows padrão (modo claro ou escuro). Use CSS/Tailwind para replicar fielmente o layout de grid dos botões, cores, fontes, tamanhos e efeitos de hover.
Layout: A tela deve ser dividida em duas partes: o teclado/visor da calculadora à esquerda, e um painel lateral retrátil ou fixo à direita listando o Histórico de cálculos.
Integração: Crie um serviço ou hook para fazer requisições HTTP (fetch ou axios) para o backend nas rotas de cálculo e de busca de histórico.
 DETALHES DO BACKEND (C# .NET) E BANCO DE DADOS

Crie o projeto dentro de uma pasta chamada calculadora-backend usando o template de Web API (dotnet new webapi).
Crie um arquivo docker-compose.yml na raiz do projeto (fora das pastas front/back) para subir um container PostgreSQL. Configure as credenciais padrão e a porta 5432.
Use Entity Framework Core (Code-First) para mapear a entidade CalculationHistory e gerar o banco/tabelas automaticamente ao iniciar (ou via migrations automáticas).
Endpoints necessários:
POST /api/calculator/calculate: Recebe um JSON com Operand1 (decimal), Operand2 (decimal) e Operator (string). Retorna o resultado, trata divisão por zero e salva no banco.
GET /api/calculator/history: Retorna a lista de histórico de operações, ordenada das mais recentes para as mais antigas.
CORS: Configure o backend para permitir requisições do frontend (localhost configurado pelo Vite).