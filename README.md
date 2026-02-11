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


<button id="botaoPdf" style="background: #2ea44f; color: white; border: none; padding: 10px 20px; border-radius: 6px; font-size: 16px; cursor: pointer;">
📄 Baixar PDF
</button>

<script>
(function() {
    const botao = document.getElementById('botaoPdf');
    if (!botao) return;

    botao.addEventListener('click', function(e) {
        e.preventDefault();

        // 1. Teste básico - remover depois de confirmar que o clique funciona
        console.log('Botão clicado!');
        alert('Clique detectado!'); // Se isso aparecer, o clique funciona

        // 2. Carrega html2pdf sob demanda
        if (typeof html2pdf === 'undefined') {
            console.log('Carregando html2pdf...');
            const script = document.createElement('script');
            script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js';
            script.onload = function() {
                console.log('html2pdf carregado, gerando PDF...');
                gerarPDF();
            };
            script.onerror = function() {
                alert('Erro ao carregar a biblioteca. Verifique sua conexão.');
            };
            document.head.appendChild(script);
        } else {
            gerarPDF();
        }

        function gerarPDF() {
            try {
                const elemento = document.querySelector('article.markdown-body') || document.body;
                const opt = {
                    margin:        [0.5, 0.5, 0.5, 0.5],
                    filename:     'documento.pdf',
                    image:        { type: 'jpeg', quality: 0.98 },
                    html2canvas:  { scale: 2, letterRendering: true, useCORS: true },
                    jsPDF:        { unit: 'in', format: 'a4', orientation: 'portrait' }
                };
                html2pdf().set(opt).from(elemento).save();
                console.log('PDF gerado com sucesso!');
            } catch (erro) {
                console.error('Erro ao gerar PDF:', erro);
                alert('Falha ao gerar o PDF: ' + erro.message);
            }
        }
    });
})();
</script>
