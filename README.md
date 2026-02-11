# Currículo

teste 5
- teste 5

![vampeta](https://veja.abril.com.br/wp-content/uploads/2025/07/vampeta-tvpop.jpg?quality=70&strip=info&w=672&h=416&crop=1)

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

<!-- Botão para PDF com formatação completa + imagens -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<div style="text-align: center; margin: 20px 0;">
  <button onclick="gerarPDFCompleto()" 
          style="background-color: #673AB7; color: white; padding: 12px 24px; 
                 border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">
    📄 PDF com formatação real + imagens
  </button>
</div>

<script>
async function gerarPDFCompleto() {
  // Configuração inicial
  const pdf = new jspdf.jsPDF({
    orientation: 'p',
    unit: 'mm',
    format: 'a4'
  });
  
  const pageWidth = pdf.internal.pageSize.getWidth();
  const margin = 20;
  const contentWidth = pageWidth - 2 * margin;
  let y = margin; // posição vertical atual
  let pageNumber = 1;

  // Função para adicionar nova página se necessário
  function checkPageSpace(requiredHeight) {
    const pageHeight = pdf.internal.pageSize.getHeight();
    if (y + requiredHeight > pageHeight - margin) {
      pdf.addPage();
      y = margin;
      pageNumber++;
    }
  }

  // Mapeamento de estilos para tags
  function getStyleForTag(tagName) {
    switch (tagName) {
      case 'H1': return { fontSize: 24, fontStyle: 'bold', lineHeight: 12, marginTop: 10, marginBottom: 6 };
      case 'H2': return { fontSize: 20, fontStyle: 'bold', lineHeight: 10, marginTop: 8, marginBottom: 5 };
      case 'H3': return { fontSize: 16, fontStyle: 'bold', lineHeight: 8, marginTop: 7, marginBottom: 4 };
      case 'H4': return { fontSize: 14, fontStyle: 'bold', lineHeight: 7, marginTop: 6, marginBottom: 3 };
      case 'H5': return { fontSize: 12, fontStyle: 'bold', lineHeight: 6, marginTop: 5, marginBottom: 2 };
      case 'H6': return { fontSize: 11, fontStyle: 'bold', lineHeight: 5, marginTop: 4, marginBottom: 2 };
      case 'P': return { fontSize: 11, fontStyle: 'normal', lineHeight: 6, marginTop: 2, marginBottom: 2 };
      case 'LI': return { fontSize: 11, fontStyle: 'normal', lineHeight: 6, marginTop: 1, marginBottom: 1, indent: 5 };
      case 'BLOCKQUOTE': return { fontSize: 10, fontStyle: 'italic', lineHeight: 5, marginTop: 3, marginBottom: 3, indent: 10 };
      case 'PRE': return { fontSize: 9, fontStyle: 'normal', lineHeight: 5, marginTop: 3, marginBottom: 3, indent: 5 };
      case 'CODE': return { fontSize: 9, fontStyle: 'normal', lineHeight: 5, marginTop: 0, marginBottom: 0 };
      default: return { fontSize: 11, fontStyle: 'normal', lineHeight: 6, marginTop: 0, marginBottom: 0 };
    }
  }

  // Função recursiva para processar nós do DOM
  async function processNode(node, indentLevel = 0) {
    if (!node) return;

    // Pular nós de script, style, etc.
    if (node.nodeType === Node.ELEMENT_NODE) {
      const tag = node.tagName;
      if (['SCRIPT', 'STYLE', 'META', 'LINK', 'HEAD'].includes(tag)) return;
    }

    // Nó de texto: escreve no PDF com a formatação herdada
    if (node.nodeType === Node.TEXT_NODE) {
      const text = node.textContent.trim();
      if (text) {
        // Aplica formatação atual (definida pelo elemento pai)
        const currentStyle = node.parentNode._pdfStyle || { fontSize: 11, fontStyle: 'normal', lineHeight: 6 };
        pdf.setFont('helvetica', currentStyle.fontStyle);
        pdf.setFontSize(currentStyle.fontSize);
        
        // Quebra de linha automática
        const lines = pdf.splitTextToSize(text, contentWidth - indentLevel * 5);
        checkPageSpace(lines.length * currentStyle.lineHeight);
        pdf.text(lines, margin + indentLevel * 5, y);
        y += lines.length * currentStyle.lineHeight;
      }
      return;
    }

    // Elemento HTML
    if (node.nodeType === Node.ELEMENT_NODE) {
      const tag = node.tagName;
      const style = getStyleForTag(tag);
      
      // Guarda o estilo no elemento para os nós filhos herdarem
      node._pdfStyle = style;

      // Se o elemento contém imagem e queremos capturá-la com html2canvas
      const hasImage = node.querySelector('img');
      const isImage = tag === 'IMG';
      
      if (isImage || (hasImage && tag === 'P')) {
        // Captura o elemento com html2canvas (somente este elemento)
        const canvas = await html2canvas(node, {
          scale: 2,
          backgroundColor: '#ffffff',
          logging: false,
          allowTaint: false,
          useCORS: true
        });
        const imgData = canvas.toDataURL('image/png');
        
        // Calcular dimensões proporcionais
        let imgWidth = contentWidth;
        let imgHeight = (canvas.height * imgWidth) / canvas.width;
        
        // Se ultrapassar altura da página, redimensiona
        const pageHeight = pdf.internal.pageSize.getHeight();
        if (imgHeight > pageHeight - margin * 2) {
          imgHeight = pageHeight - margin * 2;
          imgWidth = (canvas.width * imgHeight) / canvas.height;
        }
        
        checkPageSpace(imgHeight + 5);
        pdf.addImage(imgData, 'PNG', margin, y, imgWidth, imgHeight);
        y += imgHeight + 5;
        return;
      }

      // Processa listas: adiciona marcadores ou números
      if (tag === 'UL' || tag === 'OL') {
        let index = 1;
        for (const child of node.children) {
          if (child.tagName === 'LI') {
            // Adiciona o marcador/número antes do conteúdo
            const bullet = tag === 'UL' ? '• ' : `${index}. `;
            // Criamos um nó de texto virtual
            const textNode = document.createTextNode(bullet);
            child._bullet = bullet;
            // Processa o LI com indentação
            await processNode(child, indentLevel + 1);
            index++;
          }
        }
        return;
      }

      // Para LI, adiciona o marcador herdado
      if (tag === 'LI' && node._bullet) {
        pdf.setFont('helvetica', style.fontStyle);
        pdf.setFontSize(style.fontSize);
        pdf.text(node._bullet, margin + indentLevel * 5, y);
        // Ajusta o estilo do texto do LI (sem o marcador)
        node._pdfStyle = style;
        // Processa os filhos (texto) com indentação extra
        for (const child of node.childNodes) {
          if (child.nodeType === Node.TEXT_NODE || (child.nodeType === Node.ELEMENT_NODE && child.tagName !== 'IMG')) {
            await processNode(child, indentLevel + 1);
          }
        }
        return;
      }

      // Adiciona margem superior (espaço antes do elemento)
      if (style.marginTop) {
        y += style.marginTop;
        checkPageSpace(1);
      }

      // Processa os filhos do elemento
      for (const child of node.childNodes) {
        await processNode(child, indentLevel);
      }

      // Adiciona margem inferior
      if (style.marginBottom) {
        y += style.marginBottom;
        checkPageSpace(1);
      }
    }
  }

  // Inicia o processamento a partir do body (ou de um container específico)
  const container = document.body; // ou document.querySelector('.markdown-body') para GitHub Pages
  await processNode(container);
  
  // Salva o PDF
  pdf.save('documento_formatado.pdf');
}
</script>
