# Rocha DNS & Task Defender - início rápido

Desenvolvido por **Alexandre Rocha**. Versão 2.0.0, 01/11/2026.

## Instalar
1. Teste primeiro em uma máquina virtual descartável. Se usa o antigo Soma Defender, desinstale-o antes; não rode os dois juntos.
2. Extraia o ZIP completo. Execute **Setup.exe** como administrador e escolha Português (Brasil), English (United States), Español ou 日本語.
3. Leia a política: o monitor limpa HOSTS e aplica **8.8.8.8 e 8.8.4.4** a todas as interfaces IPv4 disponíveis. Entradas legítimas do HOSTS também são removidas e nomes internos podem deixar de resolver.
4. Configure título, mensagem e contato. Em **Anexar QR code**, selecione PDF, PNG, JPEG/JPG, BMP, GIF ou TIFF. PDF usa somente a primeira página. A prévia ao lado acompanha a edição; **Pré-visualizar janela** mostra o aviso real, sem ativar correções. Salve para concluir.
5. O monitor inicia agora e no próximo login da conta administradora usada na instalação. Não é um serviço; não roda antes do login nem automaticamente para outro usuário. Se o TI informar outra conta na elevação, a tarefa fica vinculada a essa conta.

## Ícone A.R e funcionamento
Verde: verificação concluída sem pendências. Amarelo: verificando ou pausado (confira o texto ao passar o mouse). Vermelho: alteração, aviso não reconhecido, evidência HOSTS ou falha. Clique com o botão direito para abrir, ativar, pausar, editar a mensagem, ver a caixinha ou **Encerrar**. Duplo clique abre a janela. Fechar no X ou minimizar mantém o aplicativo na área perto do relógio.

A verificação ocorre a cada 15 segundos, mais o processamento. Cada desvio de DNS corrigido também mostra o aviso, mesmo sem hosts_old_*. HOSTS é preservado como hosts_old_DDMMAAAA antes de criar outro limpo; enquanto existir qualquer hosts_old_* em etc, o aviso reaparece a cada 60 segundos. O TI deve analisar e mover esses arquivos. Backup que falha impede a correção. Não altera IPv6, proxy ou DNS seguro do navegador; Bluetooth é coberto somente quando expõe uma interface de rede IPv4.

## Editar e desinstalar
Pasta instalada: **%ProgramFiles%\RochaDefender**. Abra **MessageEditor.exe** como administrador para editar o aviso; as próximas aberturas leem os dados salvos. O QR é uma imagem anexada: não é gerado pelo campo contato nem validado como QR.

Abra **Uninstall.exe**, o atalho traduzido do menu Iniciar ou a opção em Aplicativos instalados do Windows e confirme. Remove o programa, atalhos e sua tarefa de início. Preserva configurações pessoais, imagem anexada, logs/backups, hosts_old_* e as configurações atuais de rede. DNS não é revertido. A pasta pode permanecer com os dados pessoais. Para apenas parar agora, use Encerrar; para iniciar manualmente depois, abra o programa e ative o monitor.

Logs e backups: **%LOCALAPPDATA%\RochaDefender**, no perfil executor. Antes de restaurar dados de um backup, pause o monitor. Tarefas agendadas só são desabilitadas mediante identificação exata, indicador do comando e confirmação; não são apagadas indiscriminadamente.

## Caixinha do desenvolvedor
Doação voluntária exibida ao final da instalação e disponível pelo menu. Pix: **alexandre.dirck@gmail.com**. Santander Brasil, agência **1071**, CC **01011741-4**, SWIFT/BIC **BSCHBRSP**. A caixinha não é alterada pelo editor de avisos. Verifique o favorecido no banco; o uso do app não depende de pagamento. Para transferências internacionais são necessárias instruções completas conforme moeda: https://www.santander.com.br/cambio/transferencia-internacional/

## Antes de distribuir
Executáveis sem assinatura digital. O pacote público não contém arquivos-fonte soltos, mas nenhum aplicativo cliente é inviolável contra análise ou um administrador local. A instalação restringe escrita na pasta a administradores/SYSTEM; não há serviço de autoproteção. A opção Encerrar permite parar a proteção, conforme projetado.

Testes de interface nos quatro idiomas, prévia, importação PDF, salvamento e reparos simulados passaram. Instalação/desinstalação, correções administrativas reais e retorno após reinício ainda exigem homologação em VM. O README.md contém o funcionamento completo e os limites.

Publique somente este pacote público no GitHub. O arquivo de código-fonte PRIVADO é para manutenção pelo autor.
