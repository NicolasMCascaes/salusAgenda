# Salus Agenda

> Um frontend de agendamento em saúde pensado para deixar a rotina mais simples para quem atende e para quem agenda.

O Salus Agenda organiza duas pontas da mesma jornada. De um lado, o profissional configura sua disponibilidade, acompanha a agenda e compartilha um link próprio de atendimento. Do outro, o paciente entra por esse link, faz seu cadastro quando necessário e escolhe um horário de forma direta.

Mais do que "uma agenda", a proposta do produto é reduzir atrito: menos troca manual de mensagens, menos confusão com horários e uma experiência mais clara para ambos os lados.

## O que o produto já entrega

- Login separado para paciente e profissional
- Cadastro de profissional em múltiplas etapas
- Cadastro de paciente a partir de um link de agendamento
- Configuração de horários de atendimento
- Geração de link individual para compartilhamento
- Visualização da agenda diária do profissional
- Fluxo de agendamento feito pelo paciente

## Jornada principal

1. O profissional cria a conta e entra na plataforma.
2. Define sua grade de horários disponíveis.
3. Gera um link de agendamento e compartilha com o paciente.
4. O paciente acessa esse link, valida o convite e escolhe data e horário.
5. A consulta passa a aparecer na agenda do profissional.

## Visão técnica, sem perder o foco

Este repositório guarda o frontend do produto, com a aplicação concentrada em `salusApp/`. A interface foi construída como uma SPA em React e conversa com uma API HTTP para autenticação, cadastro, disponibilidade, agendamentos e validação de links.

Principais escolhas técnicas:

- React 19 + TypeScript + Vite
- React Router para navegação entre fluxos
- React Hook Form + Zod para formulários e validações
- Axios para comunicação com a API
- Interceptor para anexar JWT e tratar sessão expirada
- Bootstrap Icons, CSS por tela e `iziToast` para feedback visual
- `vercel.json` com rewrite para manter a SPA funcionando em produção

## Estrutura do frontend

- `salusApp/src/components`: telas e fluxos principais do produto
- `salusApp/src/services/salusApi.ts`: camada de integração com a API
- `salusApp/src/services/toastService.ts`: centralização das mensagens da interface
- `salusApp/src/interfaces`: contratos tipados usados pela aplicação
- `salusApp/vercel.json`: configuração de deploy da SPA

## Como rodar localmente

```bash
cd salusApp
npm install
npm run dev
```

Para gerar build de produção:

```bash
npm run build
```

## Configuração de ambiente

O frontend usa a variável `VITE_API_URL` para descobrir onde está a API. Sem essa variável, ele tenta usar a mesma origem da aplicação.

Exemplo de `.env` dentro de `salusApp/`:

```env
VITE_API_URL=http://localhost:8080
```

Use a URL que fizer sentido para o ambiente da sua API.

## Rotas principais

- `/`: login de paciente ou profissional
- `/register`: cadastro do profissional
- `/schedulingprofessional`: agenda do profissional
- `/configure-hours`: configuração da grade de atendimento
- `/registerpatient/:linkId`: cadastro do paciente via link validado
- `/agendar`: tela de agendamento do paciente

## Estado atual do produto

O fluxo mais sólido hoje é o da operação diária: entrar, configurar horários, compartilhar link e registrar agendamentos. As visões de semana e mês já aparecem na interface, mas ainda estão em evolução em relação ao fluxo diário.

## Em uma frase

O Salus Agenda é uma base promissora para um produto de agendamento em saúde com foco em simplicidade, clareza e autonomia para profissional e paciente.
