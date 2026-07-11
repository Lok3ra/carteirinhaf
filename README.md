# Sistema de Carteirinhas Escolares

Aplicação web (arquivo único, sem servidor/backend) para gerar carteirinhas estudantis a partir de uma planilha Excel — com foto, layout configurável por ano letivo, numeração automática e impressão em folha A4 pronta para dobrar e montar.

## Funcionalidades

- **Importação por Excel/CSV**: reconhece automaticamente colunas como Nome, Data de nascimento, Nome do pai/mãe, Turma, Endereço e até 4 telefones, mesmo com cabeçalhos escritos de formas diferentes.
- **Numeração automática**: gera o número da carteirinha no formato `AATTNNNNN` (ano + turma + sequencial de 5 dígitos), com contador persistente por ano letivo.
- **Foto do aluno**: captura pela webcam ou importação de arquivo, com recorte/redimensionamento automático.
- **Layouts configuráveis por ano**: modelos Clássico, Moderno, Minimalista e Infantil, com cores, logotipo (usado também como marca d'água) e assinatura da gestão (desenhada na tela ou importada).
- **Capacidade máxima de alunos**: limite configurável (400 por padrão) por ano letivo, com aviso e bloqueio automático ao atingir o teto.
- **Impressão em folha A4**: frente e verso lado a lado, com o verso espelhado de propósito — basta dobrar o papel ao meio para montar a carteirinha corretamente. Impressão por turma inteira ou por seleção manual de até 5 alunos.
- **Exportação para Excel**: baixa uma planilha atualizada com os números e fotos já gerados, para reimportar depois sem perder nada.

## Como usar

1. Abra o `index.html` em qualquer navegador moderno (Chrome, Edge, Firefox) — não precisa de instalação nem servidor.
2. Vá em **Configurações** e preencha os dados da escola para o ano ativo.
3. Em **Importar dados**, envie a planilha com os alunos.
4. Em **Alunos**, adicione as fotos (webcam ou arquivo).
5. Em **Carteirinhas**, selecione uma turma ou até 5 alunos e clique em **Imprimir**.

## Rodando localmente

Não há build nem dependências para instalar — é um único arquivo HTML com CSS e JavaScript embutidos, usando bibliotecas via CDN (SheetJS para Excel, Google Fonts). Basta abrir o `index.html` direto no navegador ou servir a pasta com qualquer servidor estático:

```bash
# opção simples com Python
python3 -m http.server 8000
# depois acesse http://localhost:8000
```

## Publicando no GitHub Pages

1. Suba este repositório para o GitHub (veja os comandos abaixo).
2. No repositório, vá em **Settings → Pages**.
3. Em "Source", selecione a branch `main` e a pasta `/ (root)`.
4. Salve — o site ficará disponível em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

### Comandos para subir ao GitHub

```bash
git init
git add .
git commit -m "Sistema de carteirinhas escolares"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
git push -u origin main
```

## Armazenamento de dados

Os dados (alunos, fotos, configurações) ficam salvos **no navegador de quem está usando** (via `localStorage`), não em um banco de dados central nem no arquivo Excel original — o navegador não tem permissão para reescrever arquivos do computador por conta própria. Por isso:

- Os dados **não são compartilhados automaticamente** entre computadores ou navegadores diferentes.
- Limpar o cache/dados do navegador apaga as carteirinhas cadastradas.
- Use o botão **"Exportar planilha (com fotos e números)"** regularmente como backup — o arquivo gerado pode ser reimportado depois (no mesmo navegador ou em outro) sem perder números nem fotos.
- Como referência, `localStorage` costuma ter um limite de 5–10 MB por navegador; isso comporta centenas de alunos, mas em uso muito intenso (fotos de alta resolução, muitos anos acumulados) pode valer a pena evoluir para IndexedDB ou um backend próprio no futuro.

## Estrutura do repositório

```
.
├── index.html   ← aplicação completa (HTML + CSS + JS)
├── README.md
├── LICENSE
└── .nojekyll    ← evita processamento desnecessário pelo GitHub Pages
```

## Tecnologias

- HTML, CSS e JavaScript puros (sem framework, sem build).
- [SheetJS (xlsx)](https://sheetjs.com/) via CDN, para ler e gerar planilhas Excel.
- Google Fonts (Fraunces, Fredoka, Work Sans, JetBrains Mono).

## Licença

Distribuído sob a licença MIT — veja o arquivo [LICENSE](./LICENSE).
