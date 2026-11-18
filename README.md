# Minha Reforma — PWA para iPhone

Versão web instalável (PWA) do organizador de reforma. Não exige Mac para usar. O pacote contém uma aplicação estática que pode ser publicada em qualquer hospedagem HTTPS (por exemplo, GitHub Pages). O Safari precisa abrir o endereço HTTPS publicado para permitir “Adicionar à Tela de Início” e service worker/offline.

## Recursos incluídos
- Tarefas por cômodo, prioridade, data de início, edição e conclusão.
- Cronômetro por tarefa, pausa, retomada e finalização. Os intervalos são calculados por timestamps, então continuam corretos quando o Safari fica em segundo plano.
- Classificação de pausas: cansaço, falta de tempo, atividade doméstica, falta de material, imprevisto e procrastinação.
- Registro de atividades fora da reforma, incluindo atividades domésticas e descanso.
- Relatório semanal com horas de reforma, pausas e percentual de procrastinação sobre o tempo classificado.
- Controle de orçamento e despesas.
- Exportação/importação de backup JSON.
- Cache offline via service worker.

## Instalar no iPhone (sem Mac)
1. Publique o conteúdo desta pasta em um endereço HTTPS. Exemplo: crie um repositório GitHub, envie os arquivos desta pasta e habilite Settings → Pages → Deploy from a branch → `main` / root.
2. No iPhone, abra o endereço publicado no Safari.
3. Toque em Compartilhar → Adicionar à Tela de Início → Adicionar.
4. Abra pelo ícone criado. Faça um backup periódico em Mais → Exportar backup.

## Automação de chegada em casa com Atalhos
A versão PWA não tem permissão confiável para geofencing contínuo em segundo plano no iOS. Use o app Atalhos:
1. Abra Atalhos → Automação → + → Chegar.
2. Escolha o local Casa e defina a automação para executar imediatamente (se essa opção aparecer no seu iOS).
3. Adicione a ação “Mostrar Notificação” com: “Chegou em casa! Abra Minha Reforma e registre o que vai fazer: reforma, cozinhar, descansar ou outro compromisso.”
4. Opcionalmente, adicione “Abrir App”/“Abrir URL” apontando para o endereço HTTPS do PWA.

A notificação de Atalhos não lê automaticamente a agenda nem escolhe a atividade: ela convida você a registrar o que vai fazer. A detecção de chegada depende das permissões de localização do iOS e das configurações de Automação.

## Armazenamento e privacidade
Os dados são armazenados no `localStorage` do navegador no aparelho. Não há backend nem envio dos dados a terceiros. Se apagar os dados do Safari, remover o perfil do navegador ou trocar de aparelho, os dados locais podem ser perdidos; exporte backups JSON regularmente. O backup contém as informações do projeto, portanto guarde-o em local privado.

## Limitações conhecidas desta versão
- O timer usa timestamps e calcula o tempo corretamente ao voltar ao app, mas não mantém uma tela de segundos atualizando continuamente quando o iOS suspende o Safari.
- Notificações de chegada são feitas pela automação Atalhos, não pelo GPS do PWA.
- O relatório semanal é baseado em períodos efetivamente registrados; tempo sem registro não é presumido como procrastinação.
- Testar em Safari real e validar o comportamento na versão específica do iOS antes de depender dele como único registro.
