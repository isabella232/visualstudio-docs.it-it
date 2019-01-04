---
title: 'Procedura: Aggiungere controlli Chart a fogli di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 577c0531e73ad5586386c478611e57daa7e651d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967466"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Procedura: Aggiungere controlli Chart a fogli di lavoro
  È possibile aggiungere <xref:Microsoft.Office.Tools.Excel.Chart> controlli a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento. È anche possibile aggiungere <xref:Microsoft.Office.Tools.Excel.Chart> controlli in fase di esecuzione nei componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
- [Aggiungere controlli Chart in fase di progettazione](#designtime)  
  
- [Aggiungere controlli Chart in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
- [Aggiungere controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
  Per altre informazioni sulle <xref:Microsoft.Office.Tools.Excel.Chart> controlli, vedere [grafico controllo](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Aggiungere controlli Chart in fase di progettazione  
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> al foglio di lavoro nello stesso modo in cui si aggiunge un grafico dall'interno dell'applicazione.  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Tools.Excel.Chart> controllo non è disponibile il **della casella degli strumenti** o il **Zdroje dat** finestra.  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Per aggiungere un controllo host Chart a un foglio di lavoro in Excel  
  
1.  Nel **inserire** nella scheda il **grafici** fare clic su **colonna**, fare clic su una categoria di grafici e quindi scegliere il tipo di grafico desiderato.  
  
2.  Nel **Inserisci grafico** finestra di dialogo, fare clic su **OK**.  
  
3.  Nel **progettazione** nella scheda il **dati** fare clic su **selezione dati**.  
  
4.  Nel **selezionare un'origine dati** fare clic nella finestra di dialogo il **grafico** **intervallo dati** casella e deselezionare eventuali selezioni predefinite.  
  
5.  Nel **dei dati per il grafico** foglio, selezionare l'intervallo di celle contenente i dati per il grafico (celle **A5** attraverso **D8**).  
  
6.  Nel **selezionare un'origine dati** finestra di dialogo, fare clic su **OK**.  
  
##  <a name="runtimedoclevel"></a> Aggiungere controlli chart in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.Chart> controllo in modo dinamico in fase di esecuzione. I grafici creati dinamicamente non vengono salvati in modo permanente nel documento come controlli host quando il documento viene chiuso. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Aggiungere controlli chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Chart> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 I controlli Chart creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [Add Controls to Office documenti in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host foglio di lavoro basato sul foglio di lavoro aperto e quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 L'esempio prevede i requisiti seguenti:  
  
-   Dati da usare per creare il grafico, archiviati nell'intervallo da A5 a D8 nel foglio di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controllo Chart](../vsto/chart-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
