---
title: 'Procedura: Aggiungere controlli ListObject ai fogli di lavoro'
description: Informazioni su come aggiungere controlli ListObject a un foglio Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0d10d82a404ec5248e06c3d4f71d622c793f62ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634068"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Procedura: Aggiungere controlli ListObject ai fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli ListObject in fase di progettazione](#designtime)

- [Aggiungere controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli ListObject in fase di esecuzione in un progetto VSTO componente aggiuntivo](#runtimeaddin)

  Per altre informazioni sui <xref:Microsoft.Office.Tools.Excel.ListObject> controlli, vedere [Controllo ListObject](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli ListObject in fase di progettazione
 Esistono diversi modi per aggiungere controlli a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: dall'interno di Excel, dalla casella degli strumenti Visual Studio e dalla finestra Origini <xref:Microsoft.Office.Tools.Excel.ListObject> dati.  

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Per usare la barra multifunzione in Excel

1. Nel gruppo **Tabelle** della scheda **Inserisci** fare clic su **Tabella**.

2. Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.

#### <a name="to-use-the-toolbox"></a>Per usare la casella degli strumenti

1. Dalla scheda **Controlli Excel** della **casella degli strumenti** trascinare <xref:Microsoft.Office.Tools.Excel.ListObject> nel foglio di lavoro.

     Viene visualizzata la finestra di dialogo **Aggiungi controllo ListObject** .

2. Selezionare una o più celle da includere nell'elenco e fare clic su **OK**.

     Per modificare il nome predefinito, usare la finestra **Proprietà** .

#### <a name="to-use-the-data-sources-window"></a>Per usare la finestra Origini dati

1. Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

2. Trascinare una tabella dalla finestra **Origini dati** al foglio di lavoro.

     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.ListObject> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data binding e Windows Forms.](/dotnet/framework/winforms/data-binding-and-windows-forms)

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Aggiungere controlli ListObject in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in modo dinamico in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro è chiuso. Per altre informazioni, vedere [Aggiungere controlli Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice

1. Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet2":::

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Aggiungere controlli ListObject in fase di esecuzione in un progetto VSTO componente aggiuntivo
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli oggetti elenco creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene salvato e chiuso. Per altre informazioni, vedere Estendere documenti di Word e Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo ListObject a un foglio di lavoro a livello di codice

1. Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> alle celle da **A1** ad **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet8":::

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word Excel cartelle di lavoro in VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli sui Office documenti](../vsto/controls-on-office-documents.md)
- [Controllo ListObject](../vsto/listobject-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
