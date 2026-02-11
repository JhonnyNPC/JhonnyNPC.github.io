# Currículo

![vampeta](https://veja.abril.com.br/wp-content/uploads/2025/07/vampeta-tvpop.jpg?quality=70&strip=info&w=672&h=416&crop=1)

é né? za warudo

### Informações Pessoais

Nome: **João Mayer Mendes Cordeiro**\
Data de nascimento: **13/07/2009**\
Email: **joao.mayer.m.c@gmail.com**\
Telefone: **(61) 99415-2099**\
Situação atual: **Estudante**

### Sobre mim

Estudante interessado em tecnologia, programação e criação de projetos digitais. Tenho facilidade para aprender ferramentas novas, resolver problemas e trabalhar com lógica e criatividade. Busco oportunidades para desenvolver experiência prática e crescer profissionalmente.

### Formação

+ Ensino Médio incompleto\
  Colégio Católica de Brasília\
  Previsão de conclusão: 2027
+ Estudo autodidata em programação

### Experiências

**Projetos pessoais em tecnologia**
- Desenvolvimento e testes de projetos próprios
- Aprendizado prático de programação e lógica computacional
- Exploração de ferramentas digitais e criação de conteúdo

<!-- Botão definitivo - quebra de página, nome do PDF, botão invisível no PDF -->
<style>
  /* Configurações globais de impressão */
  @media print {
    /* Esconde o botão e qualquer outro elemento com classe .no-print */
    .no-print, button {
      display: none !important;
    }
    
    /* Remove margens extras do body e html */
    html, body {
      margin: 0 !important;
      padding: 0 !important;
    }
    
    /* Quebra de página ANTES de cada h1 e h2 */
    h1, h2 {
      page-break-before: always;
    }
    
    /* Mas NÃO quebra antes do primeiro h1/h2 (evita página em branco inicial) */
    h1:first-of-type, h2:first-of-type {
      page-break-before: avoid;
    }
    
    /* Ajustes de espaçamento pra não gerar páginas fantasmas */
    body {
      margin: 1.5cm !important;
    }
  }
</style>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFPerfeito()" 
          style="background-color: #D32F2F; color: white; padding: 14px 28px; 
                 border: none; border-radius: 50px; font-size: 18px; cursor: pointer; 
                 box-shadow: 0 4px 6px rgba(0,0,0,0.1); transition: 0.2s;"
          class="no-print"
          onmouseover="this.style.backgroundColor='#B71C1C'"
          onmouseout="this.style.backgroundColor='#D32F2F'">
    🧠 GERAR PDF PERFEITO (sério, agora vai)
  </button>
</div>

<script>
  function gerarPDFPerfeito() {
    // 1. Salva o título original da página
    const tituloOriginal = document.title;
    
    // 2. Define o nome do PDF baseado no primeiro H1 ou no nome da página
    const primeiroH1 = document.querySelector('h1');
    const nomePDF = primeiroH1 
      ? primeiroH1.innerText.trim() 
      : document.title || 'documento';
    
    document.title = nomePDF;
    
    // 3. Remove qualquer classe/estilo que possa causar página extra
    //    (nada específico, só garantia)
    
    // 4. Dispara a impressão com todas as regras CSS aplicadas
    window.print();
    
    // 5. Restaura o título original (opcional, mas educado)
    setTimeout(() => {
      document.title = tituloOriginal;
    }, 100);
  }
</script>
