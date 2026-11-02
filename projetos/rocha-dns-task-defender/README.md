# Rocha DNS & Task Defender

Aplicação Windows desenvolvida por **Alexandre Rocha** para diagnosticar e corrigir alterações em HOSTS e DNS IPv4, preservar backups e apresentar avisos de anomalia. Inclui revisão manual de tarefas agendadas.

**Distribuição suspensa: nenhuma versão liberada para instalação.**

Foi relatada a detecção **Trojan:Script/Ulthar.A!ml**. O bloqueio de leitura do ZIP 2.0.1 também ocorreu na máquina de desenvolvimento. [Leia o aviso de segurança e a situação da análise](AVISO-DE-SEGURANCA.md). Não restaure ou permita o arquivo e não desative as proteções para executá-lo.

## Distribuição

Os downloads 2.0.0 e 2.0.1 foram retirados da branch principal. O histórico permanece para rastreabilidade, não para uso das versões bloqueadas.

A versão 2.0.1 corrige o erro `New-NoticePanel não é reconhecido` ao abrir a configuração da mensagem no instalador compilado. A prévia ao vivo, a janela de teste e o salvamento foram verificados no mesmo tipo de execução compilada nos quatro idiomas.

As instruções de instalação nos manuais abaixo são históricas e não devem ser seguidas enquanto a suspensão estiver vigente.

## Documentação

- [Guia em português](docs/pt-BR.md)
- [English](docs/en-US.md)
- [Español](docs/es-ES.md)
- [日本語](docs/ja-JP.md)
- [Histórico de alterações](CHANGELOG.md)
- [Link para a versão atual](VERSAO-ATUAL.md)

## Antes de utilizar

- Padrão DNS IPv4: **8.8.8.8 e 8.8.4.4**. A política de HOSTS limpo também remove entradas legítimas; valide a compatibilidade com a rede.
- O monitor inicia após o login da conta administradora configurada. Não é um serviço de sistema e não atua antes do login nem automaticamente para outros usuários.
- O ícone **A.R** indica os estados verde, amarelo e vermelho. **Encerrar** no menu do ícone para a execução atual; não desinstala.
- Para desinstalar, utilize **Uninstall.exe**, o atalho do menu Iniciar ou Aplicativos instalados. Logs, backups, configurações pessoais e o estado atual de DNS/HOSTS são preservados.
- Os executáveis ainda não têm assinatura digital. Instalação, desinstalação, correções administrativas reais e retorno após reinício precisam de homologação em VM.

## Código e distribuição

Esta pasta distribui somente o pacote público compilado e sua documentação. O código-fonte permanece privado. O empacotamento e as permissões não tornam o programa inviolável contra engenharia reversa ou acesso administrativo.

A versão não recebeu uma licença de código aberto. Consulte o arquivo `NOTICE.txt` dentro do pacote e a documentação de uso.
