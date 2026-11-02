# Histórico de alterações

## Suspensão de downloads — 01/11/2026

- Recebido relato de detecção Trojan:Script/Ulthar.A!ml durante download, com item removido do cache do Opera.
- Confirmada recusa do Windows ao ler o ZIP 2.0.1 na máquina de desenvolvimento por detecção de ameaça.
- Retirados os ZIPs 2.0.0 e 2.0.1 da branch principal; histórico, documentação e hashes preservados.
- Não foi concluída análise que permita classificar como falso positivo; não foi gerada versão alternativa para contornar o bloqueio.
- Consulte AVISO-DE-SEGURANCA.md. Nenhuma versão está liberada.

## 2.0.1 — 01/11/2026

- Corrige a resolução de `New-NoticePanel` no instalador e editor compilados. As funções agora são carregadas no escopo principal da execução.
- Inicia o temporizador da prévia somente depois da inicialização e trata falhas da prévia sem deixar uma exceção não tratada da interface.
- Teste de regressão reproduz o erro original e verifica a correção no ambiente compilado para os quatro idiomas, incluindo prévia ao vivo, abertura da janela e salvamento com anexo.
- Testes gerais de interface, menu e motor de monitoramento continuam passando. A homologação administrativa completa em VM permanece pendente.

## 2.0.0 — 01/11/2026

- Nome público: Rocha DNS & Task Defender.
- Ícone A.R com estados verde, amarelo e vermelho.
- Instalação em português do Brasil, inglês dos EUA, espanhol e japonês.
- Editor de aviso com título, mensagem, contato, prévia ao vivo e abertura da janela real.
- Anexo de QR em PDF (primeira página), PNG, JPEG, BMP, GIF e TIFF.
- Caixinha de doação independente do editor de avisos.
- Distribuição compilada, com código-fonte mantido privado.
- Instalador, tarefa de início após login, permissões da pasta e desinstalador.
- Monitoramento de HOSTS e DNS IPv4, backups e avisos de atendimento.

### Validação

Passaram os testes locais de interface e idiomas, prévia, salvamento, importação PDF, menu do ícone e correções simuladas. A instalação/desinstalação e as alterações administrativas reais, inclusive após reinício, ainda precisam de homologação em máquina virtual.
