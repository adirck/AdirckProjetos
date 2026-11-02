# Validação da edição 3.0.0

Data: 02/11/2026.

- Compilação C#/.NET Framework sem runtime PowerShell ou scripts embutidos.
- Interface, prévias e editor nos quatro idiomas: passaram.
- Três políticas DNS, validação dos dois IPv4 personalizados, transferência da escolha e preservação ao salvar o aviso: passaram em testes isolados.
- Núcleo de backup, HOSTS, falhas por interface, modo automático e restauração de padrão: passaram com arquivos/adaptadores simulados, sem alterações na rede real do desenvolvimento.
- Quatro MSI convencionais: validação de tabelas e extração administrativa com saída 0 e hashes correspondentes aos binários.
- Microsoft Defender local: ZIP final verificado com MpCmdRun.exe, resultado found no threats. Resultado pontual, sem assinatura digital ou parecer formal do fornecedor.
- Autor confirmou instalação/desinstalação e abertura completa com a prévia em uma máquina. Não equivale a aprovação em todas as lojas ou comprovação das políticas novas em todas as redes.

Pendente de validação ampliada pelo autor/TI: execução real de DNS personalizado/DHCP, início após login/reinício, recuperação e rollback e compatibilidade com os produtos de segurança de outras máquinas.

As versões 2.0.0 e 2.0.1 continuam suspensas. Nenhuma proteção foi desativada nem foram criadas exclusões. Se houver nova detecção, interrompa o teste e preserve os detalhes do alerta.
