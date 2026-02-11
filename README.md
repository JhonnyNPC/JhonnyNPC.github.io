# Currículo

- teste 4

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


<button id="botaoPdfMultiplasPaginas" style="background: #2ea44f; color: white; border: none; padding: 10px 20px; border-radius: 6px; font-size: 16px; cursor: pointer;">
📄 Baixar PDF (várias páginas)
</button>

<script>
(function() {
    const botao = document.getElementById('botaoPdfMultiplasPaginas');
    if (!botao) return;

    botao.addEventListener('click', function(e) {
        e.preventDefault();

        if (typeof html2pdf === 'undefined') {
            const script = document.createElement('script');
            script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js';
            script.onload = gerarPDF;
            script.onerror = () => alert('Erro ao carregar a biblioteca.');
            document.head.appendChild(script);
        } else {
            gerarPDF();
        }

        function gerarPDF() {
            try {
                const elemento = document.querySelector('article.markdown-body') || document.body;

                const opt = {
                    margin:        [0.4, 0.4, 0.4, 0.4], // polegadas
                    filename:     'documento_completo.pdf',
                    image:        { type: 'jpeg', quality: 0.98 },
                    html2canvas:  { scale: 2, letterRendering: true, useCORS: true },
                    jsPDF:        { unit: 'in', format: 'a4', orientation: 'portrait' },
                    pagebreak:    { mode: ['css', 'legacy'] } // 🟢 ESSENCIAL PARA MÚLTIPLAS PÁGINAS
                };

                html2pdf().set(opt).from(elemento).save();
            } catch (erro) {
                console.error(erro);
                alert('Erro: ' + erro.message);
            }
        }
    });
})();
</script>
