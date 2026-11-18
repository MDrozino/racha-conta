# Racha Conta

Site para dividir contas (casa, bar, viagem…), cada conta só entre quem participa.

- `index.html` – a página (HTML/JS puro).
- `api/interpretar.js` – função serverless do Vercel que usa a IA (Google Gemini) para transformar a fala/texto do usuário em contas preenchidas.

## Funcionalidades
- Pessoas e contas editáveis; cada conta escolhe quem participa.
- Divisão igual ou por quantidade (ex.: Maria 3 cervejas, João 1).
- Valor aceita “3x12” (= R$ 36).
- Taxa de serviço (%) proporcional ao consumo.
- “Pago por”: calcula saldos e o mínimo de transferências.
- Dados zeram ao abrir a página; “Copiar link” compartilha as contas; “Copiar resumo” gera texto para o WhatsApp.
- IA (“Prefere digitar?” e, em breve, microfone): preenche o formulário; contas incertas ficam em amarelo.

## Proteções da IA (`api/interpretar.js`)
- Só aceita POST vindo do próprio site; limite de pedidos por IP.
- Texto ≤ 1.000 caracteres; áudio ≤ 2 MB e só tipos de áudio.
- Instrução fixa: a IA só extrai contas, ignora instruções dentro da fala e responde `fora_do_escopo` para qualquer outra coisa.
- Temperatura 0 e resposta obrigatoriamente no formato JSON definido.
- O servidor valida tudo de novo: descarta campos extras, limita valores/quantidades/tamanhos e remove símbolos de código. Nunca repassa texto livre da IA.

## Configurar a IA no Vercel
1. Crie uma chave grátis em https://aistudio.google.com → **Get API key**. **Não** ative faturamento (assim nunca há cobrança; ao acabar a cota, o site avisa e segue funcionando manualmente).
2. No Vercel: projeto → **Settings → Environment Variables** → adicione `GEMINI_API_KEY` com a chave (Production e Preview).
3. Opcional: `GEMINI_MODEL` com os modelos a tentar, em ordem, separados por vírgula (padrão: `gemini-3.8-flash,gemini-3.5-flash-lite`).
4. Faça um novo deploy (push) para a variável valer.

## Deploy
Conectado ao GitHub: cada push na `main` publica no Vercel. Pushes em outras branches geram um link de teste (preview).
