# 🥗 NutriPlan AI - Plataforma de Planos Alimentares Automatizados

## 📖 Sobre o Projeto

NutriPlan AI é uma plataforma web que gera **planos alimentares personalizados em PowerPoint** em 30 segundos, baseada em mais de 20 parâmetros individuais. Elimina a necessidade de criar planos manualmente, economizando horas de trabalho.

## ✨ Funcionalidades

### ✅ Implementado

- **Formulário Inteligente de 4 Etapas**
  - Dados pessoais (idade, peso, altura, sexo)
  - Rotina e objetivos (atividade física, meta, horários)
  - Preferências alimentares (dieta, restrições, alergias)
  - Suplementação (opcional)

- **Cálculos Nutricionais Automáticos**
  - Taxa Metabólica Basal (TMB) - Fórmula Harris-Benedict
  - Calorias diárias (TDEE) com ajuste por atividade
  - Macronutrientes (proteínas, carboidratos, gorduras)
  - Adaptação automática por objetivo (perder/ganhar/manter)

- **Plano Semanal Variado**
  - 7 dias completamente diferentes
  - 5 refeições por dia (café, lanche manhã, almoço, lanche tarde, jantar)
  - Banco de dados com 15+ opções de refeições
  - Rotação inteligente sem repetições

- **Lista de Compras Automática**
  - Extração de ingredientes do plano semanal
  - Organização por categorias (proteínas, carboidratos, frutas, vegetais, etc.)
  - Eliminação de duplicatas

- **PowerPoint Profissional**
  - 11 slides com design premium
  - Paleta de cores verde saudável
  - Download automático
  - Formato editável (.pptx)

## 🚀 Como Usar

### Opção 1: Uso Local (Desenvolvimento/Teste)

1. **Baixe os arquivos**
   ```bash
   # Baixe nutrition_platform.html
   ```

2. **Abra no navegador**
   ```bash
   # Simplesmente clique duas vezes no arquivo HTML
   # ou arraste para o navegador
   ```

3. **Preencha o formulário**
   - Complete todas as 4 etapas
   - Clique em "Gerar Meu Plano Alimentar"

4. **Receba seu plano**
   - Arquivo PowerPoint será baixado automaticamente
   - Abra com PowerPoint, Google Slides ou Keynote

### Opção 2: Deploy em Produção

#### GitHub Pages (GRÁTIS)

1. **Crie repositório no GitHub**
   ```bash
   # Novo repositório: nutriplan-ai
   ```

2. **Faça upload do HTML**
   ```bash
   git init
   git add nutrition_platform.html
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/seu-usuario/nutriplan-ai.git
   git push -u origin main
   ```

3. **Ative GitHub Pages**
   - Settings → Pages
   - Source: main branch
   - Salve

4. **Acesse sua plataforma**
   ```
   https://seu-usuario.github.io/nutriplan-ai/nutrition_platform.html
   ```

#### Vercel (GRÁTIS)

1. **Instale Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Deploy**
   ```bash
   vercel
   # Siga as instruções
   ```

3. **Pronto!**
   - URL: https://nutriplan-ai.vercel.app

#### Netlify (GRÁTIS)

1. **Arraste e solte**
   - Acesse: https://app.netlify.com/drop
   - Arraste o arquivo HTML
   - Pronto!

2. **Domínio customizado** (opcional)
   - Site settings → Domain management
   - Adicione seu domínio

## 🔧 Estrutura Técnica

### Frontend
- **HTML5 + CSS3**: Interface responsiva e moderna
- **JavaScript Vanilla**: Sem dependências de frameworks
- **PptxGenJS 3.12.0**: Geração de PowerPoint client-side

### Algoritmos

**1. Cálculo de TMB (Taxa Metabólica Basal)**
```javascript
// Homens
TMB = 10 × peso(kg) + 6.25 × altura(cm) - 5 × idade + 5

// Mulheres
TMB = 10 × peso(kg) + 6.25 × altura(cm) - 5 × idade - 161
```

**2. Cálculo de TDEE (Total Daily Energy Expenditure)**
```javascript
// Multiplicadores por nível de atividade
Sedentário: TMB × 1.2
Leve: TMB × 1.375
Moderado: TMB × 1.55
Intenso: TMB × 1.725
Atleta: TMB × 1.9

// Ajuste por objetivo
Perder peso: TDEE × 0.85 (-15%)
Manter peso: TDEE × 1.0
Ganhar massa: TDEE × 1.15 (+15%)
```

**3. Distribuição de Macronutrientes**
```javascript
// Ganhar massa / Muito ativo
Proteína: 30% das calorias
Carboidratos: 45%
Gorduras: 25%

// Perder peso
Proteína: 35%
Carboidratos: 35%
Gorduras: 30%

// Manutenção
Proteína: 25%
Carboidratos: 50%
Gorduras: 25%
```

### Banco de Dados de Refeições

**Estrutura**
```javascript
mealDatabase = {
  breakfast: [
    {
      name: "Nome da refeição",
      items: ["ingrediente 1", "ingrediente 2", ...],
      tags: ["tag1", "tag2"]
    }
  ],
  snacks: [...],
  lunch: [
    {
      name: "Nome",
      protein: "descrição proteína",
      carb: "descrição carboidrato",
      veggies: "descrição vegetais",
      tags: [...]
    }
  ],
  dinner: [...]
}
```

**Expansão Fácil**
- Adicione novos objetos ao array
- Sistema automaticamente rotaciona opções
- Tags facilitam filtragem por restrições

## 💰 Monetização

### Integração com Hotmart (Recomendado)

1. **Crie conta no Hotmart**
   - https://www.hotmart.com/pt-br

2. **Crie produto**
   - Tipo: Ebook/Digital
   - Preço: R$ 47,00
   - Comissão: 9,9% + R$ 1,49

3. **Obtenha link de checkout**
   ```javascript
   // Adicione antes do botão "Gerar Plano"
   const checkoutUrl = "https://pay.hotmart.com/SEU_CODIGO";
   
   // Modifique função generatePlan()
   function generatePlan() {
     // Validação...
     
     // Redireciona para checkout
     window.location.href = checkoutUrl + "?email=" + userData.email;
   }
   ```

4. **Configure webhook**
   - Hotmart → Ferramentas → Postback
   - URL: sua-url.com/webhook
   - Após pagamento aprovado, gera plano

### Integração com Stripe

```javascript
// Adicione Stripe.js
<script src="https://js.stripe.com/v3/"></script>

// Configure checkout
const stripe = Stripe('pk_test_SUA_CHAVE_PUBLICA');

async function generatePlan() {
  // Criar sessão de checkout
  const response = await fetch('/create-checkout-session', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ price: 4700 }) // R$ 47,00 em centavos
  });
  
  const session = await response.json();
  
  // Redirecionar para checkout
  stripe.redirectToCheckout({ sessionId: session.id });
}
```

## 🎨 Customização

### Alterar Cores da Plataforma

```css
/* Edite no <style> do HTML */

/* Gradiente do header */
background: linear-gradient(135deg, #SUA_COR_1 0%, #SUA_COR_2 100%);

/* Cor dos botões */
.btn {
  background: linear-gradient(135deg, #SUA_COR_1 0%, #SUA_COR_2 100%);
}
```

### Alterar Cores do PowerPoint

```javascript
// Procure no JavaScript:
const primary = "2C5F2D";    // Verde escuro
const secondary = "84B59F";  // Verde claro
const accent = "50808E";     // Azul acinzentado

// Substitua pelos códigos hex das suas cores (sem #)
```

### Adicionar Novas Refeições

```javascript
// Localize: const mealDatabase = { ... }

// Adicione ao array desejado:
breakfast: [
  // ... refeições existentes
  {
    name: "Sua Nova Refeição",
    items: [
      "Ingrediente 1",
      "Ingrediente 2",
      "Ingrediente 3"
    ],
    tags: ["tag1", "tag2"]
  }
]
```

### Personalizar Textos

Busque e substitua os textos diretamente no HTML:
- `<h1>🥗 NutriPlan AI</h1>` → Seu nome
- `<p>Seu plano alimentar personalizado em segundos</p>` → Sua mensagem
- `Dra. Marion Nestle` → Seu nome/marca

## 📊 Analytics e Métricas

### Google Analytics 4

```html
<!-- Adicione antes de </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Eventos Personalizados

```javascript
// Quando usuário gera plano
gtag('event', 'generate_plan', {
  'event_category': 'engagement',
  'event_label': userData.goal,
  'value': dailyCalories
});

// Quando usuário completa formulário
gtag('event', 'complete_form', {
  'event_category': 'conversion',
  'event_label': 'step_4'
});
```

## 🔐 Segurança e Privacidade

### LGPD Compliance

Adicione antes do formulário:

```html
<div class="privacy-notice">
  <p>
    <input type="checkbox" id="privacy_consent" required>
    <label for="privacy_consent">
      Concordo com o processamento dos meus dados para geração do plano alimentar 
      conforme <a href="/politica-privacidade.html">Política de Privacidade</a>
    </label>
  </p>
</div>
```

### Disclaimer Médico

```html
<div class="disclaimer">
  <p>⚠️ <strong>Aviso Importante:</strong> Este plano é gerado automaticamente 
  para fins informativos. Consulte um nutricionista ou médico antes de 
  fazer mudanças significativas em sua dieta.</p>
</div>
```

## 🐛 Troubleshooting

### Problema: PowerPoint não baixa

**Solução 1:** Verifique se o navegador permite downloads
- Chrome: Settings → Privacy → Site Settings → Downloads → Allow

**Solução 2:** Teste em outro navegador
- Firefox, Edge, Safari

**Solução 3:** Verifique console de erros
- F12 → Console → Procure erros em vermelho

### Problema: Cálculos incorretos

**Verifique:**
- Campos estão preenchidos corretamente
- Peso em KG, altura em CM
- TMB não pode ser negativo

**Debug:**
```javascript
// Adicione após cálculos
console.log('TMB:', tmb);
console.log('Calorias:', dailyCalories);
console.log('Macros:', macros);
```

### Problema: Refeições repetindo

**Causa:** Banco de dados pequeno
**Solução:** Adicione mais opções ao mealDatabase

## 📝 Roadmap

### Versão 1.1 (30 dias)
- [ ] Adicionar 10 novas opções de refeições
- [ ] Implementar modo noturno
- [ ] Adicionar calculadora de água necessária
- [ ] Exportar também em PDF

### Versão 1.2 (60 dias)
- [ ] Backend para salvar planos gerados
- [ ] Login com Google
- [ ] Histórico de planos anteriores
- [ ] Comparação de progresso

### Versão 2.0 (90 dias)
- [ ] App mobile (React Native)
- [ ] Notificações de lembretes
- [ ] Integração com MyFitnessPal
- [ ] Marketplace de receitas

## 🤝 Contribuindo

Este é um projeto comercial, mas feedback é sempre bem-vindo!

**Como reportar bugs:**
1. Descreva o problema
2. Passos para reproduzir
3. Comportamento esperado vs. atual
4. Screenshots (se aplicável)

## 📄 Licença

© 2026 NutriPlan AI. Todos os direitos reservados.

Este software é proprietário. Não é permitido:
- Redistribuir o código
- Criar trabalhos derivados para venda
- Usar para competir diretamente

**Permitido:**
- Uso pessoal
- Customização para seu próprio negócio
- White label (com licença)

## 💬 Suporte

**Documentação Completa:**
- `GUIA_NEGOCIO_NUTRIPLAN.md` - Estratégias de negócio e monetização

**Links Úteis:**
- PptxGenJS Docs: https://gitbrent.github.io/PptxGenJS/
- Hotmart: https://hotmart.com
- Stripe: https://stripe.com

---

**Desenvolvido com ❤️ para revolucionar a nutrição personalizada**

*Última atualização: Janeiro 2026*
