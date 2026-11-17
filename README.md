# Racha Conta

Site estático (um único `index.html`, sem backend) para dividir as contas da casa no fim do mês.

## Funcionalidades
- Moradores editáveis.
- Cada conta escolhe **quem participa** (ex.: streaming só entre 2).
- Divisão **igual** ou **por peso** (ex.: quarto maior = 1,5).
- "Pago por": calcula saldos e o **mínimo de transferências** (quem paga quanto pra quem).
- Divisão em centavos sem perder nenhum centavo no arredondamento.
- Salva no navegador (localStorage).
- **Copiar link**: gera um link com todos os dados embutidos para mandar aos outros moradores.
- **Copiar resumo**: texto pronto para colar no WhatsApp.

## Deploy grátis no Vercel
**Opção 1 – sem instalar nada:** acesse https://vercel.com/new, crie um projeto e arraste a pasta `racha-conta` (ou use https://vercel.com/drop, se disponível).

**Opção 2 – via GitHub:** suba a pasta para um repositório, em vercel.com → *Add New → Project* → importe o repo. Framework: *Other*, sem build command. Cada `git push` faz deploy automático.

**Opção 3 – CLI:**
```bash
npm i -g vercel
cd racha-conta
vercel --prod
```

Também funciona igual em Netlify, Cloudflare Pages ou GitHub Pages (é só um HTML).
