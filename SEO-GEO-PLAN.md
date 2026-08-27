# Mozy Construction — SEO + GEO Build Plan
> Consolidado dos agentes SEO (gustavo) e GEO (seo-geo), 2026-08-15. Guia de construção do site estático.

## Estrutura de URLs (pretty URLs, folder/index.html)
```
/                                  Home
/services/                         Hub de serviços
/services/full-home-renovation/    CARRO-CHEFE
/services/kitchen-remodeling/
/services/bathroom-remodeling/
/services/flooring/
/services/painting/                (interior + exterior)
/services/pavers-outdoor/
/services/doors-sliding-door-repair/
/services/handyman/
/locations/                        Hub de áreas
/locations/orlando/                Central FL — pilar
/locations/broward-county/         South FL — pilar (cobre Fort Lauderdale, Hollywood, Pembroke Pines)
/locations/miami/                  South FL — pilar
/projects/                         Portfólio (filtrável por serviço e mercado)
/about/                            Marca + licença CGC 1535189
/contact/  ou  /free-estimate/     Form → Zoho CRM (CTA global)
```
**Fase 2 (só com dados de volume reais):** páginas `/services/{serviço}/{cidade}/` de alto ticket (home-renovation, kitchen, bathroom). NÃO criar as 8×3 combinações de cara — vira doorway/thin content.

## Regra anti-canibalização (a mais importante)
Serviço = conteúdo mestre escrito UMA vez. Localização = página com contexto local REAL (bairros, projetos daquele mercado, notas de permit/HOA). Nunca clonar o corpo trocando só o nome da cidade. Só publicar página local quando houver (a) volume real e (b) pelo menos 1 projeto real naquele mercado.

## Templates de title / meta
| Tipo | Title (≤60) | Meta (150-160) |
|---|---|---|
| Home | General Contractor in Orlando & South Florida \| Mozy Construction | Licensed general contractor (FL CGC 1535189) serving Orlando, Broward & Miami. Full home renovation, kitchens, baths & more. Free estimate — (754) 271-6203. |
| Service | {Service} Contractor in Florida \| Mozy Construction | Professional {service} by a licensed & insured Florida contractor. Serving Orlando & South Florida. Free estimate — (754) 271-6203. |
| Service+City | {Service} in {City}, FL \| Mozy Construction | Looking for {service} in {City}? Licensed & insured GC, CGC 1535189. Free {city} estimate — (754) 271-6203. |
| Location | {City} General Contractor & Remodeling \| Mozy Construction | Mozy Construction serves {City} with full renovation, kitchen & bath remodeling and more. Licensed FL contractor. Free estimate — (754) 271-6203. |

## Schema JSON-LD
- Site-wide `<head>`: GeneralContractor (name, url, telephone, email, areaServed [Orlando/Broward/Miami], hasCredential CGC 1535189, makesOffer). JÁ implementado na home.
- Cada service page: `Service` (serviceType, provider @id, areaServed, description).
- `/faq/` e service pages: `FAQPage` (usar os blocos abaixo, texto igual ao visível).
- Todas: `BreadcrumbList`.

## Regras de escrita p/ GEO (citabilidade em ChatGPT/Perplexity/AI Overviews)
1. Todo H2/H3 é uma pergunta do jeito que o homeowner digita.
2. Resposta direta nos primeiros 40-60 palavras; bloco total 134-167 palavras.
3. Bloco autossuficiente: repetir nome + licença + área dentro do bloco.
4. Um fato/um número por afirmação (CGC 1535189, (754) 271-6203, "2 to 4 weeks").
5. Texto em HTML puro (não injetado por JS) — garante crawl por GPTBot/ClaudeBot/PerplexityBot.
6. Tabelas para comparações (custos por serviço, cidades) — IA extrai e cita bem.
7. Licença em TEXTO (não só no logo) em toda service page + footer.
8. Autoria real em blog/FAQ: "Reviewed by Moises Silva, Owner, Mozy Construction (CGC 1535189)".
9. "Last updated [data]" nas páginas de FAQ/serviço.

## FAQ / Answer-blocks (conteúdo pronto p/ colar — 12 blocos)
Estão em [faq-answers.md](faq-answers.md). Reusar os relevantes por service/location page.

## Off-site (prioridade p/ visibilidade local + IA)
1. **Google Business Profile** — maior peso. Preencher tudo, licença na descrição, coletar/responder reviews.
2. **YouTube** — maior correlação com citação em IA. Vídeos before/after com título descritivo ("Kitchen Remodel Orlando FL — Before & After | Mozy Construction").
3. **Reddit** — participação genuína em r/orlando, r/Miami, r/HomeImprovement.
4. **Diretórios com NAP + licença consistentes** — Yelp, Angi, HomeAdvisor, BBB, Houzz (consistência > volume de backlink).
5. **Instagram @mozy_construction** — sameAs.

## ⚠️ PENDÊNCIAS QUE DEPENDEM DO DONO (bloqueiam SEO local)
1. **Endereço** p/ verificação do Google Business Profile (físico ou Service Area Business sem endereço visível?).
2. **1 ou 2 perfis GBP** — 1 SAB cobrindo as 3 áreas (seguro) vs 2 perfis (só se houver 2 endereços reais; senão risco de suspensão).
3. **Liberar DataForSEO** p/ volume/KD reais antes de construir páginas serviço×cidade.
4. **Fotos reais de obra** por mercado (destravam as páginas locais e o portfólio) + reviews reais do Google.
5. **Confirmar** que CGC cobre FL inteiro (é "Certified" = estadual; ok) — só validar.
