# Histórico de segurança e situação da distribuição

**Atualização de 02/11/2026:** a edição C# 3.0.0 está publicada para validação pelo autor. O Defender local não detectou ameaças no ZIP desta edição; isso não é garantia universal ou parecer formal. [Situação atual](VERSAO-ATUAL.md). As versões 2.0.0 e 2.0.1 continuam suspensas.

## Registro original de suspensão

**Data: 01/11/2026. Versões afetadas: 2.0.0 e 2.0.1.**

Foi relatada a detecção **Trojan:Script/Ulthar.A!ml** pelo Microsoft Defender durante o download. A imagem aponta um item no cache do navegador Opera, com status removido. Isso, sozinho, não demonstra infecção persistente do computador nem identifica qual executável dentro do pacote foi classificado.

Na máquina de desenvolvimento, a tentativa de ler o ZIP 2.0.1 também foi recusada pelo Windows com a informação de que o arquivo contém vírus ou software possivelmente indesejado. A consulta aos detalhes do Defender e a execução de uma verificação específica não puderam ser concluídas por falta de permissão. **Não há resultado de varredura que permita declarar o pacote seguro.**

## Orientação aos usuários

- Não baixe, execute, restaure da quarentena nem permita o aplicativo enquanto esta investigação estiver aberta.
- Não desative antivírus, SmartScreen, proteção contra adulteração ou políticas corporativas; não crie exclusões para este projeto.
- Se já executou alguma versão, encerre o monitor e informe seu TI. Faça a verificação pelo produto de segurança da organização, seguindo o procedimento local.
- Preserve a captura do alerta, a data, a versão baixada e os detalhes da detecção. Não restaure o arquivo apenas para coletar essas informações.

## Situação da distribuição

Os arquivos ZIP das versões 2.0.0 e 2.0.1 foram retirados da branch principal por precaução. Os diretórios, documentação, hashes e histórico Git foram preservados para rastreabilidade. **Cópias em commits antigos ou em links já compartilhados não devem ser usadas.**

A correção de interface da versão 2.0.1 não é uma validação de segurança ou compatibilidade com antivírus. Os testes funcionais anteriores não substituem essa análise.

## Próximas etapas

1. Revisar código, dependências e processo de compilação em ambiente de análise apropriado.
2. Submeter o artefato específico e os detalhes da detecção à Microsoft, como desenvolvedor, pelo canal oficial: https://www.microsoft.com/en-us/wdsi/filesubmission
3. Considerar falso positivo somente após evidência técnica e resposta do fornecedor; não presumir isso pelo nome genérico da detecção.
4. Antes de nova distribuição, concluir análise de segurança, testes de instalação em VM e avaliação de assinatura digital.

**Registro de 01/11/2026:** não havia nova versão liberada. Até 02/11/2026, não houve envio ao portal da Microsoft nem parecer formal. Consulte a atualização no topo para a edição 3.0.0.

## Atualização: prévia nativa 3.0.0-preview.1

Foi preparada uma nova implementação C# sem interpretador PowerShell ou scripts embarcados, com MSI convencionais. Os testes isolados, a extração dos quatro MSI e as verificações locais pelo Microsoft Defender passaram, sem detecção nos novos artefatos. Trata-se de prévia compartilhada diretamente com o autor para homologação; nenhum novo binário foi liberado nesta branch. [Situação e limites dos testes](versoes/3.0.0-preview.1/README.md).

Não houve contorno ou desativação do antivírus. O novo resultado não prova que as detecções das versões antigas eram falsos positivos e não substitui assinatura ou parecer formal da Microsoft.

