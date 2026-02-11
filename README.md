# Projects!

Todos os meus projetos em um só lugar, em caso de repositorios dedicados o README.md tanto se encontra aqui quanto no repositorio dedicado do projeto, e aqui você encontrará um link te redirecionando ao repositorio escolhido

## Índice
- [Curso de Programação Voltado Para Celular](https://jhonny1307.github.io/#curso-de-programação-voltado-para-celular)
- [MD2PDF](https://jhonny1307.github.io/#md2pdf)

## Curso de Programação Voltado Para Celular

- Em Andamento, Aguarde! [Playlist (Youtube)](https://www.google.com/)

## MD2PDF

Adiciona um botão a pagina que transforma toda a pagina em pdf, ignora o botão (ele mesmo) e funciona totalmente client-side, utilizando a função ```window.print()``` como visivel a seguir (caso esteja visualizando pelo site), você pode clicar nele e baixar o pdf deste projeto junto dos outros que aqui se encontram sem demais problemas!
- Uso recomendado para ```Github Pages```

<style>
  @media print {
    .no-print, button {
      display: none !important;
    }
    
    html, body {
      margin: 0 !important;
      padding: 0 !important;
    }
    
    h1, h2 {
      page-break-before: always;
    }
    
    h1:first-of-type, h2:first-of-type {
      page-break-before: avoid;
    }
    
    body {
      margin: 1.5cm !important;
    }
  }
</style>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFPerfeito()" 
          style="background-color: #000000; color: white; padding: 14px 28px; 
                 border: none; border-radius: 50px; font-size: 18px; cursor: pointer; 
                 box-shadow: 0 4px 6px rgba(0,0,0,0.1); transition: 0.2s;"
          class="no-print"
          onmouseover="this.style.backgroundColor='#808080'"
          onmouseout="this.style.backgroundColor='#000000'">
    Download PDF
  </button>
</div>

<script>
  function gerarPDFPerfeito() {
    const tituloOriginal = document.title;
    const primeiroH1 = document.querySelector('h1');
    const nomePDF = primeiroH1 
      ? primeiroH1.innerText.trim() 
      : document.title || 'documento';
    document.title = nomePDF;
    window.print();
    
    setTimeout(() => {
      document.title = tituloOriginal;
    }, 100);
  }
</script>

Caso deseje usar este botão em seus projetos, o codigo dele pode ser visto abaixo, basta copiar e colar no arquivo markdown desejado para gerar o botão na posição que o colocou.

```
<style>
  @media print {
    .no-print, button {
      display: none !important;
    }
    
    html, body {
      margin: 0 !important;
      padding: 0 !important;
    }
    
    h1, h2 {
      page-break-before: always;
    }
    
    h1:first-of-type, h2:first-of-type {
      page-break-before: avoid;
    }
    
    body {
      margin: 1.5cm !important;
    }
  }
</style>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFPerfeito()" 
          style="background-color: #000000; color: white; padding: 14px 28px; 
                 border: none; border-radius: 50px; font-size: 18px; cursor: pointer; 
                 box-shadow: 0 4px 6px rgba(0,0,0,0.1); transition: 0.2s;"
          class="no-print"
          onmouseover="this.style.backgroundColor='#B71C1C'"
          onmouseout="this.style.backgroundColor='#D32F2F'">
    Download PDF
  </button>
</div>

<script>
  function gerarPDFPerfeito() {
    const tituloOriginal = document.title;
    const primeiroH1 = document.querySelector('h1');
    const nomePDF = primeiroH1 
      ? primeiroH1.innerText.trim() 
      : document.title || 'documento';
    document.title = nomePDF;
    window.print();
    
    setTimeout(() => {
      document.title = tituloOriginal;
    }, 100);
  }
</script>
```

