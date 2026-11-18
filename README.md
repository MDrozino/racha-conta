<div align="center">

# 🧾 Racha Conta

**Divida as contas da casa, do bar ou de qualquer rolê, cada uma só entre quem participa.**
Fale ou digite as contas, e o formulário se preenche sozinho.

[![Acessar o site](https://img.shields.io/badge/Acessar-rachaconta--ten.vercel.app-2f6f5e?style=for-the-badge)](https://rachaconta-ten.vercel.app)

![HTML](https://img.shields.io/badge/HTML%2FJS-puro-e34f26?style=flat-square)
![Vercel](https://img.shields.io/badge/Deploy-Vercel-000?style=flat-square&logo=vercel)
![Gemini](https://img.shields.io/badge/IA-Google%20Gemini-4285f4?style=flat-square&logo=googlegemini&logoColor=white)
![Custo](https://img.shields.io/badge/Custo-R%24%200-2f6f5e?style=flat-square)

</div>

---

## 💡 Por que existe

Quem mora com outras pessoas conhece o fim do mês: aluguel, condomínio, internet, luz, streaming… e nem todo mundo participa de todas as contas. O Racha Conta resolve isso em segundos, mostrando **quanto cada um paga** e **quem deve transferir quanto para quem**.

## ✨ Funcionalidades

| | |
|---|---|
| 🎙️ **Ditado por voz** | Toque no microfone e fale. O texto aparece na tela, você confere e toca em **Preencher**. |
| 🤖 **Preenchimento com IA** | A IA transforma a fala em pessoas, contas, valores, quem consumiu o quê e quem pagou. Contas incertas ficam em **amarelo** para conferir. |
| 👥 **Cada conta, seus participantes** | Marque quem divide cada conta, em partes iguais ou **por quantidade/peso** (ex.: quarto maior = 1,5). |
| 🧮 **Atalho no valor** | Digite `3x12` e vira R$ 36,00. |
| 🍽️ **Taxa de serviço** | Os 10% do garçom são divididos proporcionalmente ao consumo de cada um. |
| 🔁 **Acertos automáticos** | Informe quem pagou cada conta e veja o **mínimo de transferências** para todo mundo ficar quite. |
| 📲 **Compartilhar** | **Copiar resumo** gera um texto pronto para o WhatsApp; **Copiar link** manda as contas preenchidas para os outros. |
| 🏠 **Modo casa** | Em [`/?casa`](https://rachaconta-ten.vercel.app/?casa), salve um **modelo da sua casa** no próprio celular. Ele já abre preenchido todo mês. |
| 🔒 **Privacidade** | O site normal não guarda nada: ao abrir, começa do zero. O modelo da casa fica só no navegador do seu aparelho. |

## 🗣️ Exemplo

> *"Estamos eu, João, Maria e Pedro. A Maria tomou 3 cervejas e o Pedro 2, cada cerveja era 12 reais. Eu e o João dividimos uma porção de 40. A pizza de 80 foi de todo mundo. O João pagou tudo, e tem mais 10% do garçom."*

O formulário é preenchido sozinho e os acertos aparecem na hora:

```
Maria → João   R$ 61,60
Pedro → João   R$ 48,40
Eu    → João   R$ 44,00
```

## 🛡️ Proteções da IA

A IA **não conversa**: ela só preenche o formulário. Para garantir isso:

- **Formato fixo:** a resposta precisa seguir um esquema JSON definido, com temperatura 0.
- **Fora do escopo:** pedidos que não são contas (ex.: *"me escreve um código"*) são recusados.
- **Fala tratada como dado:** instruções escondidas na fala são ignoradas.
- **Validação no servidor:** tudo é conferido de novo antes de chegar ao site. Campos extras são descartados, valores e tamanhos são limitados e símbolos de código são removidos.
- **Limites de uso:** só aceita chamadas do próprio site, com limite de pedidos por pessoa e tamanho máximo de texto e áudio.
- **Sem cobrança:** usa o plano gratuito do Gemini, sem faturamento ativado. Se a cota do dia acabar, o site avisa e continua funcionando no modo manual.

## 🧱 Como é feito

```
racha-conta/
├── index.html          # o site inteiro: HTML, CSS e JavaScript puros
├── api/
│   └── interpretar.js  # função serverless: fala/texto → Gemini → JSON validado
├── vercel.json         # tempo máximo da função
└── README.md
```

- **Front-end:** um único `index.html`, sem frameworks e sem build.
- **Voz:** ditado do navegador (Web Speech API, pt-BR). Em navegadores sem ditado, o áudio é gravado, convertido para WAV e enviado à IA.
- **Back-end:** uma função serverless no Vercel que chama o **Google Gemini** (Flash-Lite primeiro, por ser rápido, e Flash como reserva).
- **Cálculos em centavos:** a divisão nunca perde nem sobra centavo.

## 🚀 Rodando o seu

1. Faça um fork deste repositório e importe no [Vercel](https://vercel.com/new) (Framework: *Other*, sem build command).
2. Crie uma chave gratuita em [Google AI Studio](https://aistudio.google.com) → **Get API key**. Não ative faturamento.
3. No Vercel, vá em **Settings → Environment Variables** e adicione:

   | Variável | Valor |
   |---|---|
   | `GEMINI_API_KEY` | sua chave do AI Studio |
   | `GEMINI_MODEL` *(opcional)* | modelos em ordem, separados por vírgula (padrão: `gemini-3.5-flash-lite,gemini-3.8-flash`) |

4. Faça um novo deploy. Pronto!

> Sem a chave, o site funciona normalmente no modo manual. Só o preenchimento por IA fica desativado.

---

<div align="center">
Feito para acabar com a planilha do fim do mês. 🍻
</div>
