---
title: 'Procedura: Aggiungere controlli ListObject a fogli di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc0b8a8b22459c386d856c3992059f390f363aea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868979"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Procedura: Aggiungere controlli ListObject a fogli di lavoro
  È possibile aggiungere <xref:Microsoft.Office.Tools.Excel.ListObject> controlli a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 È anche possibile aggiungere <xref:Microsoft.Office.Tools.Excel.ListObject> controlli in fase di esecuzione nei progetti di componente aggiuntivo VSTO.  
  
 Questo argomento descrive le attività seguenti:  
  
- [Aggiungere controlli ListObject in fase di progettazione](#designtime)  
  
- [Aggiungere controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
- [Aggiungere controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
  Per altre informazioni sulle <xref:Microsoft.Office.Tools.Excel.ListObject> controlli, vedere [controllo ListObject](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Aggiungere controlli ListObject in fase di progettazione  
 Esistono diversi modi per aggiungere <xref:Microsoft.Office.Tools.Excel.ListObject> controlli a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: Da Excel, Visual Studio **casella degli strumenti**e dal **Zdroje dat** finestra.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>Per usare la barra multifunzione in Excel  
  
1.  Nel gruppo **Tabelle** della scheda **Inserisci** fare clic su **Tabella**.  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
#### <a name="to-use-the-toolbox"></a>Per usare la casella degli strumenti  
  
1.  Dalla scheda **Controlli Excel** della **casella degli strumenti**trascinare <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi controllo ListObject** .  
  
2.  Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.  
  
     Per modificare il nome predefinito, usare la finestra **Proprietà** .  
  
#### <a name="to-use-the-data-sources-window"></a>Per usare la finestra Origini dati  
  
1.  Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).  
  
2.  Trascinare una tabella dalla finestra **Origini dati** al foglio di lavoro.  
  
     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.ListObject> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data binding e Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Aggiungere controlli ListObject in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo in modo dinamico in fase di esecuzione. e creare in questo modo i controlli host in risposta a eventi. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro è chiuso. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Aggiungere controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene salvato e chiuso. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice  
  
1.  Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [ListObject (controllo)](../vsto/listobject-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
