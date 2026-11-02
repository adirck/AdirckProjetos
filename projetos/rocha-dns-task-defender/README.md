# Rocha DNS & Task Defender

Aplicação desenvolvida por **Alexandre Rocha**. Implementação Windows Forms em C#, sem PowerShell ou scripts embutidos.

## Versão 3.0.0 - primeira edição pública para validação

**[Baixar Windows x64](https://github.com/adirck/AdirckProjetos/releases/download/v3.0.0/Rocha-DNS-Task-Defender-3.0.0-Windows-x64.zip)**

[Release e arquivos de verificação](https://github.com/adirck/AdirckProjetos/releases/tag/v3.0.0) | [Manual de instalação e uso](docs/3.0.0/LEIA-ME.md) | [SHA256](versoes/3.0.0/SHA256SUMS.txt)

Extraia todo o ZIP e abra Setup.exe. Escolha o idioma e uma política: Google (8.8.8.8 / 8.8.4.4), automático/DHCP ou dois DNS personalizados. Configure o aviso e confira a prévia antes de salvar. Ao atualizar, encerre a cópia anterior pelo ícone A.R.

## Recursos

- Português BR, inglês EUA, espanhol e japonês.
- Ícone A.R com estados verde, amarelo e vermelho.
- Monitoramento de HOSTS e DNS IPv4 a cada 15 segundos, com backup antes de corrigir.
- Restaura a política DNS selecionada. No automático, remove DNS manual e aceita os servidores recebidos da rede; não altera o IP fixo da placa.
- Aviso único personalizável com contato e QR, mais o motivo específico da correção.
- QR anexado como PDF (primeira página), PNG, JPEG, BMP, GIF ou TIFF, com prévia ao vivo e janela de teste.
- Revisão de tarefas agendadas; nenhuma tarefa é apagada indiscriminadamente.
- Instaladores MSI convencionais, início após login da conta administradora configurada, editor e desinstalador.

## Validação e limites

O autor relatou instalação, desinstalação e abertura completa bem-sucedidas em uma máquina com a prévia. Os testes locais dos quatro idiomas, três políticas simuladas, backups, avisos e extração dos MSI passaram. O Defender local não detectou ameaças no ZIP desta edição. Isso não garante o mesmo resultado em todos os produtos de segurança nem constitui aprovação formal da Microsoft/ESET.

**A validação ampliada está em andamento.** Especialmente DNS automático/personalizado em redes reais, retorno após reiniciar e procedimentos de recuperação devem ser conferidos pelo TI. Executáveis ainda sem assinatura digital. Não ignore detecções nem crie exclusões para continuar.

Requer Windows 10 build 19041 ou posterior / Windows 11 x64 e .NET Framework 4.8. Não é serviço: não atua antes do login ou automaticamente em outras contas. HOSTS limpo remove entradas legítimas e DNS público pode afetar nomes internos. Não altera IPv6, proxy ou DNS seguro do navegador.

## Documentação e histórico

- [Manual da edição 3.0.0](docs/3.0.0/LEIA-ME.md)
- [Relatório de validação](versoes/3.0.0/VALIDACAO.md)
- [Histórico de alterações](CHANGELOG.md)
- [Versão atual](VERSAO-ATUAL.md)
- [Aviso de segurança das versões antigas](AVISO-DE-SEGURANCA.md)

As versões 2.0.0 e 2.0.1 continuam suspensas e não devem ser utilizadas. Os manuais antigos em docs são históricos; use o manual da edição 3.0.0.

## Distribuição

Somente pacote compilado e documentação são públicos. Código-fonte permanece privado. Não há licença de código aberto aplicada ao código; consulte NOTICE.txt no pacote. Configurações pessoais e evidências não são publicadas.
