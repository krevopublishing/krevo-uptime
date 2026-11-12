# krevo-uptime

Sonda externa de disponibilidade da plataforma KREVO. A cada 15 minutos, o GitHub Actions testa por
HTTPS os endpoints públicos de saúde (`/health`) dos subdomínios de `krevo.company`. Uma falha gera
e-mail do GitHub e notificação no app GitHub Mobile.

O repositório é público para que os minutos do GitHub Actions não consumam a cota do repositório
privado. Ele contém só URLs públicas, nenhum segredo.

## Desativação após 60 dias

O GitHub desativa workflows agendados de repositórios públicos depois de 60 dias sem atividade. Por isso:

1. todo dia 1º um job reativa o agendamento pela API e faz um commit de manutenção (`.keepalive`);
2. o vigia do servidor confere a cada hora se a sonda continua rodando e envia alerta se ela parar;
3. reativação manual: `gh workflow enable probe.yml --repo krevopublishing/krevo-uptime`.
