---
title: Exportar relatórios para PDF
description: Saiba como exportar um relatório do Power BI para PDF.
author: mihart
manager: kvivek
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: c18257f1f4e4e3f325c8d4d895e3b6abf88e900c
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794977"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Exportar relatórios do Power BI para PDF
Com o Power BI, você pode publicar seu relatório em formato PDF e criar facilmente um documento baseado no relatório do Power BI. Quando você **exportar para PDF**, cada página no relatório do Power BI se torna uma página individual no seu documento PDF.

## <a name="how-to-export-your-power-bi-report-to-pdf"></a>Como exportar um relatório do Power BI para o PDF
No serviço do Power BI, selecione um relatório para exibi-lo na tela. Você também pode selecionar um relatório na Página Inicial, Aplicativos ou em qualquer outra seção no painel de navegação esquerdo.

1. Selecione **Arquivo** > **Exportar para PDF** na barra de menus.

    ![Seleção de Arquivo na barra de menus e seta apontando para Exportar para PDF](media/end-user-pdf/power-bi-export-pdf.png)

    É exibida uma barra de progresso no canto superior direito. Exportar pode levar alguns minutos e você pode continuar a trabalhar no Power BI enquanto o relatório está sendo exportado.

    ![Mensagem de progresso da exportação](media/end-user-pdf/power-bi-export-message.png)

    Depois de concluído, o banner de notificação muda para informá-lo de que o serviço do Power BI terminou o processo de exportação.

2. O arquivo estará disponível quando o navegador exibir os arquivos baixados. Na imagem a seguir, ele é mostrado como uma faixa de download na parte inferior da janela do navegador.

    ![Local do arquivo baixado](media/end-user-pdf/power-bi-save-file.png)

E isso é tudo para ele. Você pode baixar o arquivo e abri-lo com qualquer visualizador de PDF, como o disponível no Microsoft Edge.


## <a name="limitations-and-considerations"></a>Limitações e considerações
Há algumas considerações e limitações para ter em mente ao trabalhar com o recurso **Exportar para o PDF**.

- A interatividade na sessão, assim como o realce e filtragem, drill down e assim por diante, ainda não têm suporte ao exportar para o PDF. O PDF exportado mostra os visuais originais como eles tivessem sido salvos no relatório. Se você aplicou filtros e segmentações de dados e deseja que isso seja preservado na exportação, salve o relatório e faça a exportação.

* No momento, não há suporte para **visuais do R**. No PDF, esses elementos visuais estarão em branco e exibirão uma mensagem de erro.  

* Há suporte para **visuais personalizados** que foram **certificados**. Para obter mais informações sobre visuais personalizados certificados, incluindo como obter um visual personalizado certificado, consulte [Certificando um visual personalizado](../power-bi-custom-visuals-certified.md). Não há suporte para visuais personalizados que não tenham sido certificados. No PDF, eles serão exibidos com uma mensagem de erro.   

* No momento, não é possível exportar relatórios com mais de 30 páginas de relatório.

* O processo de exportar o relatório para o PDF pode levar alguns minutos para ser concluído, seja paciente. Os fatores que podem afetar o tempo necessário incluem a estrutura do relatório e a carga atual no serviço do Power BI.

* Se o item de menu **Exportar para o PDF** não estiver disponível no serviço do Power BI, provavelmente será porque seu administrador de locatários desabilitou o recurso. Entre em contato com seu administrador de locatários para obter detalhes.

* As imagens da tela de fundo serão cortadas com a área delimitadora do gráfico. É altamente recomendável que você remova as imagens de tela de fundo antes de exportar para o PDF.

* Os relatórios que são propriedade de um usuário fora de seu domínio de locatário do Power BI (como um relatório de alguém fora de sua organização e compartilhado com você) não podem ser publicados no PDF.

* Se você compartilhar um dashboard com alguém fora de sua organização (e, portanto, um usuário que não está em seu locatário do Power BI), esse usuário não poderá exportar os relatórios associados ao painel compartilhado para o PDF. Por exemplo, se você for aaron@contoso.com, poderá compartilhar com cassie@cohowinery.com. No entanto, cassie@cohowinery.com não poderá exportar os relatórios associados para o PDF.

* O serviço Power BI usa a configuração de idioma do Power BI como o idioma para a exportação do PDF. Para obter ou definir sua preferência de idioma, selecione o ícone de engrenagem **Configurações** > **Geral** > **Idioma**.

## <a name="next-steps"></a>Próximas etapas
[Imprimir um relatório](end-user-print.md)