# Currículo

- teste 2

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
  Previsão de conclusão: 2027\
+ Estudo autodidata em programação

### Experiências

**Projetos pessoais em tecnologia**
- Desenvolvimento e testes de projetos próprios
- Aprendizado prático de programação e lógica computacional
- Exploração de ferramentas digitais e criação de conteúdo


<button onclick="
    if (typeof html2pdf !== 'undefined') {
        gerarPDF();
    } else {
        var script = document.createElement('script');
        script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js';
        script.onload = gerarPDF;
        document.head.appendChild(script);
    }
    function gerarPDF() {
        var elemento = document.body; // 👈 troque pelo ID do elemento que deseja (ex: '#conteudo')
        var opt = {
            margin:        [0.5, 0.5, 0.5, 0.5], // superior, direito, inferior, esquerdo (em polegadas)
            filename:     'documento.pdf',
            image:        { type: 'jpeg', quality: 0.98 },
            html2canvas:  { scale: 2, letterRendering: true, useCORS: true, logging: true },
            jsPDF:        { unit: 'in', format: 'a4', orientation: 'portrait' }
        };
        html2pdf().set(opt).from(elemento).save();
    }
" style="background: #2ea44f; color: white; border: none; padding: 10px 20px; border-radius: 6px; font-size: 16px; cursor: pointer;">
📄 Baixar PDF (sem cortes)
</button>
