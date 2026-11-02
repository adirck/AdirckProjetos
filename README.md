# AdirckProjetos

Central de distribuição e documentação dos projetos de **Alexandre Rocha**.

> **Atualização (02/11/2026):** a edição C# **3.0.0** está disponível para validação pelo autor. As versões **2.0.0 e 2.0.1 continuam suspensas**. [Consulte o histórico de segurança](projetos/rocha-dns-task-defender/AVISO-DE-SEGURANCA.md).

Cada projeto tem sua própria pasta. As atualizações são adicionadas como novas versões, preservando o histórico e os pacotes anteriores.

## Projetos

| Projeto | Versão atual | Situação | Acesso |
| --- | --- | --- | --- |
| Rocha DNS & Task Defender | 3.0.0 | Primeira edição pública C#, em validação | [Página do projeto](projetos/rocha-dns-task-defender/README.md) |

## Organização

```text
projetos/
  rocha-dns-task-defender/
    README.md
    VERSAO-ATUAL.md
    CHANGELOG.md
    docs/
    versoes/
      2.0.1/
        Rocha-DNS-Task-Defender-2.0.1-Windows.zip
        SHA256SUMS.txt
modelos/
  novo-projeto/
    README.md
    VERSAO-ATUAL.md
    CHANGELOG.md
    docs/
    versoes/
```

## Acrescentar um projeto

1. Copie `modelos/novo-projeto` para `projetos/nome-do-projeto`.
2. Preencha o nome, finalidade, autor, requisitos, instalação e desinstalação.
3. Coloque a documentação em `docs/` e o primeiro pacote em `versoes/1.0.0/`.
4. Atualize a tabela de projetos desta página.

Use nomes curtos, sem espaços ou acentos, para os nomes das pastas. Cada processo ou aplicativo distinto deve ficar em sua própria pasta.

## Publicar uma atualização

1. Crie uma nova pasta em `versoes/`, por exemplo `2.0.1` ou `2.1.0`.
2. Adicione o pacote de distribuição e seu hash SHA256.
3. Registre as alterações e a situação de testes em `CHANGELOG.md`.
4. Atualize `VERSAO-ATUAL.md`, a documentação aplicável e esta tabela.
5. Mantenha os pacotes anteriores nas suas pastas originais. Não substitua silenciosamente um arquivo de versão publicada.

Sugestão de numeração: correção `2.0.2`, nova funcionalidade compatível `2.1.0`, mudança incompatível `3.0.0`.

## Conteúdo público e privado

Este repositório é **público**. Publique somente materiais autorizados para distribuição: pacotes compilados, instruções e arquivos de verificação.

Não envie código-fonte que deva permanecer privado, senhas, tokens, certificados privados, logs, backups, dados de clientes ou configurações pessoais. Os dados de doação do desenvolvedor fazem parte do pacote público do Rocha Defender por decisão do autor.

Cada projeto informa suas condições de uso e suas limitações. Estar disponível aqui não significa que já foi homologado para produção.
