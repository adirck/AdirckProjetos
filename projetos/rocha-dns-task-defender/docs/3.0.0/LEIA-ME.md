# Rocha DNS & Task Defender 3.0.0

**Aplicação desenvolvida por Alexandre Rocha.** Primeira edição pública da implementação C#, publicada em 02/11/2026 para validação pelo autor. Windows 10 build 19041 ou posterior / Windows 11, x64, .NET Framework 4.8.

## Instalar ou atualizar

1. Se há uma cópia aberta, clique no ícone A.R perto do relógio e escolha **Encerrar**. Não deixe duas versões monitorando ao mesmo tempo.
2. Extraia **todo** o ZIP em uma nova pasta. Mantenha Setup.exe e os quatro MSI juntos.
3. Abra **Setup.exe**, escolha o idioma e clique em Próximo.
4. Escolha somente uma política DNS:
   - **Google:** 8.8.8.8 e 8.8.4.4.
   - **Automático (DHCP):** limpa DNS manual e aceita os servidores fornecidos pela rede. Não altera o endereço IP fixo da placa.
   - **Personalizado:** preencha DNS principal e secundário IPv4 válidos e diferentes. Os campos aparecem somente nessa opção e habilitam Próximo quando válidos.
5. Leia a política e autorize a elevação normal de administrador do Windows. Não altere as proteções para continuar se algum produto de segurança bloquear o arquivo.
6. Ao abrir o editor, configure o aviso, contato e QR opcional. Confira a prévia ao vivo e a janela de pré-visualização. Salve para registrar o início automático e ativar o monitor.
7. A janela de doação é opcional e não condiciona o uso. Depois, confira o ícone A.R na área de notificações, inclusive nos ícones ocultos.

Os MSI são pacotes do Windows Installer. Use o Setup.exe para conduzir as telas de idioma/DNS e a configuração final. Se abrir um MSI diretamente, os arquivos poderão ser instalados sem concluir a configuração ou ativar o monitor.

## O que o programa faz

- Verifica a política DNS salva e o HOSTS a cada 15 segundos, acrescidos do processamento e backup.
- Restaura Google ou o par personalizado se houver desvio. No automático, remove DNS configurado manualmente e aceita mudanças legítimas dos servidores recebidos automaticamente.
- Faz backup antes de alterar; se o backup falhar, aquela correção fica bloqueada. Não altera IPv6, proxy ou DNS seguro de navegadores.
- Preserva HOSTS alterado como hosts_old_DDMMAAAA e cria um arquivo hosts limpo, sem extensão. Entradas legítimas também são removidas pela política de limpeza; revise a compatibilidade com sistemas internos.
- Exibe uma mensagem única, com os dados personalizados, e uma seção **Motivo do aviso**. Ela informa o que realmente aconteceu: ajuste de DNS Google, personalizado ou automático, limpeza de HOSTS, evidência pendente ou falha. Não afirma que houve invasão só por existir configuração diferente.
- Enquanto houver hosts_old_* na pasta etc, o aviso reaparece a cada 60 segundos. Fechar a mensagem não resolve essa pendência. O TI deve analisar e mover todos esses arquivos para armazenamento de evidências; a aplicação não autentica quem os retirou.
- Se o estado inicial já estiver conforme, sem marcadores ou falhas, não há aviso de alteração. Na primeira ativação, configurar uma placa fora do padrão escolhido é uma correção e abre o aviso correspondente.
- Lista tarefas agendadas para revisão. Desabilitar exige identificação exata, indicador de comando e confirmação. Não apaga tarefas indiscriminadamente.

## Ícone, editor e inicialização

Ícone A.R: **verde** após verificação sem pendência; **amarelo** verificando ou pausado; **vermelho** para alteração, pendência ou falha. Botão direito oferece abrir, ativar, pausar, editar, doação e Encerrar no idioma escolhido. Fechar ou minimizar a janela mantém o aplicativo rodando.

O início automático é vinculado ao login da conta administradora configurada. **Não é serviço:** não roda antes do login nem automaticamente em outras contas. Se outra conta for usada na elevação, a tarefa pode ficar vinculada a ela. Usuários de loja sem privilégios administrativos precisam de planejamento pelo TI.

MessageEditor.exe edita o aviso. Política de DNS pode ser alterada na janela principal com privilégios administrativos. A edição da mensagem preserva a política DNS. Próximos avisos leem o texto salvo; uma janela já aberta mantém o conteúdo até ser reaberta.

QR aceito em PDF (primeira página), PNG, JPEG/JPG, BMP, GIF e TIFF. O arquivo é normalizado localmente para PNG. Não é gerado pelo campo contato nem validado como QR. Limite de 25 MB e 10000 pixels por dimensão. Doações são independentes e não podem ser alteradas pelo editor de avisos.

## Pastas e desinstalação

- Programa: `%ProgramFiles%\RochaDefender3`.
- Aviso, política e QR: `%ProgramData%\RochaDefender3`, com escrita restrita a administradores/SYSTEM.
- Logs e backups: `%LOCALAPPDATA%\RochaDefender3` do usuário executor.
- Log de instalação: `%LOCALAPPDATA%\RochaDefender3\InstallerLogs` do usuário que abriu o Setup. Em caso de falha, use **Abrir log da instalação**.
- Tarefa própria: `RochaDefender-Monitor-v3`.

Desinstale por **Aplicativos instalados**, pelo atalho localizado no menu Iniciar ou por Uninstall.exe na pasta instalada. O Windows Installer remove os arquivos e a rotina nativa pede o encerramento do monitor e remove sua tarefa. Configurações pessoais, QR, logs/backups, hosts_old_* e o estado atual da rede são preservados. Não há reversão automática do DNS/HOSTS.

## Segurança e validação

Não há PowerShell, scripts embutidos, desativação de antivírus ou alterações nas permissões da Temp. Google/personalizado usam a API Windows SetInterfaceDnsSettings; automático usa diretamente o utilitário oficial netsh.exe para a origem DNS IPv4, sem shell ou script.

O autor relatou instalação/desinstalação e abertura completa bem-sucedidas em uma máquina com a prévia. Testes locais de interface nos quatro idiomas, políticas simuladas, backups e extração dos MSI passaram. A versão 3.0.0 ainda requer validação ampliada, especialmente para DNS personalizado/DHCP em redes reais e início após reiniciar.

Os executáveis estão **sem assinatura digital**. A verificação local pelo Microsoft Defender não detectou ameaças no pacote desta edição; isso é um resultado pontual, não uma garantia universal ou um parecer formal da Microsoft/ESET. Nenhum arquivo foi submetido a esses fornecedores para aprovação. Se ocorrer detecção, interrompa e guarde os detalhes; não libere nem exclua a proteção para executar.

As versões 2.0.0 e 2.0.1 permanecem suspensas por detecção anterior. O novo resultado não demonstra que eram falsos positivos. Código-fonte permanece privado; compilar não impede engenharia reversa ou controle por um administrador.

## Caixinha do desenvolvedor

Doação voluntária: Pix **alexandre.dirck@gmail.com**. Banco Santander Brasil, agência **1071**, conta corrente **01011741-4**, SWIFT/BIC **BSCHBRSP**. Confira o favorecido no banco. Transferências internacionais precisam das instruções completas conforme moeda: https://www.santander.com.br/cambio/transferencia-internacional/
