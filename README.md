# Chamada de Profissionais por Voz

Página web simples para chamar profissionais do salão pela caixa de som conectada ao
computador, sem precisar gritar pelo ambiente. A recepção filtra a profissional pela
função, escolhe quem chamar e o tipo de mensagem, e o navegador fala o chamado em voz
alta (pt-BR), repetindo duas vezes.

- **100% gratuita**, sem backend e sem dependências pagas.
- Interface (`index.html`) com CSS e JS embutidos; a lista da equipe fica num arquivo
  separado e simples, `profissionais.js`.
- Funciona aberta com **duplo clique** no PC ou publicada no **GitHub Pages**.
- Voz pela **Web Speech API** nativa do navegador — nenhum arquivo de áudio.
- Busca por nome, filtro por função com contadores e cartões grandes para toque/clique.

> **Arquivos:** mantenha `index.html` e `profissionais.js` **na mesma pasta**. Ao publicar,
> suba os dois na raiz do repositório.

---

## 1. Como editar a equipe

Abra o `profissionais.js` em qualquer editor de texto. Ele contém apenas o array
`PROFISSIONAIS`:

```js
const PROFISSIONAIS = [
  { nome: "Nádia",  funcao: "Cabeleireira" },
  { nome: "Leila",  funcao: "Manicure" },
  { nome: "Erica",  funcao: "Designer" },
  // ...
];
```

- Cada profissional é uma linha `{ nome: "...", funcao: "..." }`.
- Para **adicionar**, copie uma linha e troque o nome e a função.
- Para **remover**, apague a linha inteira.
- Cada pessoa tem **uma única função**.
- Os botões de filtro (chips) por função são gerados **automaticamente** a partir
  desta lista — não há uma segunda lista para manter sincronizada.

### Corrigir a pronúncia de um nome

Se a voz pronuncia um nome de forma estranha, adicione o campo opcional **`falar`** com
a grafia "fonética" — o nome real continua aparecendo na tela; **só a fala muda**:

```js
{ nome: "Sibelly", funcao: "Manicure", falar: "Cibele" },
```

Acima, a tela mostra "Sibelly", mas a voz diz "Cibele".

Salve o arquivo e recarregue a página no navegador. (Se `profissionais.js` faltar ou não
carregar, a página usa uma pequena lista de exemplo embutida como segurança.)

---

## 2. Como usar localmente (PC da recepção)

1. Salve `index.html` e `profissionais.js` (na mesma pasta) no PC da recepção.
2. Abra com **duplo clique** — abrirá no navegador padrão (de preferência Chrome ou Edge).
3. Garanta que a **caixa de som esteja conectada ao PC como saída de áudio padrão**
   (o áudio sai do aparelho que dispara o chamado).

**Fluxo de uso (3 passos):**
1. **Filtrar por função** — clique em um chip (ou em "Todas").
2. **Escolher a profissional** — toque no botão dela.
3. **Escolher a mensagem** — toque numa das duas opções; o chamado é falado em voz
   alta, duas vezes, com o botão pulsando enquanto fala.

> O primeiro toque na página "destrava" o som em alguns navegadores (sobretudo no
> celular). Como toda fala parte de um clique, isso já fica resolvido no uso normal.

---

## 3. Como publicar no GitHub Pages

1. Crie um repositório no GitHub e suba `index.html` **e** `profissionais.js` **na raiz**
   (o arquivo precisa se chamar exatamente `index.html` para o GitHub Pages servir
   automaticamente).
2. No repositório: **Settings → Pages**.
3. Em **Branch**, selecione `main` e a pasta raiz (`/root`) → **Save**.
4. Aguarde alguns instantes e acesse o link gerado (algo como
   `https://seu-usuario.github.io/seu-repositorio/`) no PC e no celular.

---

## 4. Observação importante sobre o som

O áudio sai do **aparelho que dispara** o chamado:

- O **PC da recepção** (ligado à caixa de som) é o disparador principal — o chamado
  sai pela caixa.
- O **celular** toca no próprio alto-falante, a menos que esteja pareado/conectado à
  mesma caixa de som.

---

## 5. Observação sobre a voz

É a **voz sintética do sistema operacional** (no Windows há vozes em português como
"Daniel" (masculina) e "Maria" (feminina)). É adequada para avisos no ambiente, mas
**não é uma locução profissional**.

No topo da página, ao lado do volume, há um **seletor de voz** com botões para cada voz
em português instalada no aparelho (♂ masculina, ♀ feminina). A voz **masculina é o
padrão**; basta tocar em outro botão para trocar, e a escolha fica lembrada no navegador.
As vozes disponíveis dependem do que está instalado no PC/celular — para adicionar mais
no Windows: **Configurações → Hora e idioma → Fala**.

---

## Privacidade (LGPD)

Por discrição, a mensagem 2 diz apenas **"sua cliente chegou e aguarda na recepção"**,
sem anunciar o nome da cliente em voz alta.

Se um dia quiser reativar o nome da cliente, adicione um campo de texto opcional no
Passo 3 e uma terceira mensagem do tipo
*"[Nome], sua cliente [nome da cliente] aguarda na recepção."* — usando o nome digitado
somente quando o campo estiver preenchido.

---

## Mensagens atuais

1. **"[Nome], comparecer à recepção."**
2. **"[Nome], sua cliente chegou e aguarda na recepção."**

## Volume da voz

No topo da página há um **controle de volume** para a voz do chamado. O padrão é **95%**;
arraste o controle para deixá-la mais alta ou mais baixa em relação à música que toca no
mesmo PC. O ajuste é lembrado no próprio navegador.

> Observação técnica: o navegador controla **apenas o volume da própria voz** (0–100%),
> não o da música (que toca em outro aplicativo). Por isso o ajuste é manual — equilibre
> conforme o volume da música no momento. Evite deixar muito baixo, ou o chamado não será
> ouvido sobre a música.

## Compatibilidade

Testado para Chrome/Edge no Windows (cenário principal) e navegadores de celular
(uso secundário). Layout responsivo, com botões grandes para toque e clique.
