# 3.0.0-preview.1 - reformulação nativa em teste controlado

**Sem liberação pública para produção.** Os binários desta prévia são compartilhados diretamente com o autor para homologação em ambiente de teste. Nenhum pacote desta versão está publicado nesta pasta.

## Mudanças

- Aplicação Windows Forms em C#/.NET Framework, sem PowerShell, scripts embutidos ou carregador de scripts.
- Configuração IPv4 pela API documentada SetInterfaceDnsSettings; tarefas pela interface COM do Windows.
- MSI convencionais, localizados nos quatro idiomas. Editor com prévia, importação PDF/imagem, avisos, bandeja e doação preservados.
- Windows 10 build 19041 ou posterior / Windows 11, x64, .NET Framework 4.8.

## Validação realizada em 01/11/2026

- Testes isolados do núcleo e da interface passaram nos quatro idiomas.
- Extração administrativa dos quatro MSI com saída 0 e hashes correspondentes aos binários de origem.
- Verificações locais pelo Microsoft Defender dos executáveis, MSI e ZIP final: **found no threats**.

Isso não é garantia universal, assinatura digital ou parecer formal da Microsoft. Instalação/desinstalação completas em VM, registro da tarefa de início, retorno após login e correções reais de rede permanecem pendentes. Os executáveis estão sem assinatura.

As versões 2.0.0 e 2.0.1 continuam suspensas. Não houve desativação de proteções, exclusão no antivírus nem restauração das versões antigas para produzir esta prévia. [Aviso de segurança](../../AVISO-DE-SEGURANCA.md).
