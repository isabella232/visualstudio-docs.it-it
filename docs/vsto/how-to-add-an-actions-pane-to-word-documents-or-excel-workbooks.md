---
title: Aggiungere il riquadro Azioni ai documenti di Word o Excel cartelle di lavoro
description: Per aggiungere un riquadro azioni a un documento di Microsoft Office Word o a una cartella di lavoro Microsoft Excel, è necessario creare prima un controllo utente Windows Form.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a30853d0d685f4b916993b5784cc1158304115385442e7ceb4709f8c17a4e739
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424210"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel
  Per aggiungere un riquadro azioni a un documento Microsoft Office Word o a una cartella di lavoro Microsoft Excel, creare prima un controllo utente Windows Form. Aggiungere quindi il controllo utente alla proprietà del campo <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` (Word) o del campo `ThisWorkbook.ActionsPane` (Excel) nel progetto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="creating-the-user-control"></a>Creazione del controllo utente
 La procedura seguente illustra come creare un controllo utente in un progetto word o Excel progetto. Aggiunge anche un pulsante al controllo utente che scrive testo nel documento o nella cartella di lavoro quando si fa clic su di esso.

#### <a name="to-create-the-user-control"></a>Per creare il controllo utente

1. Aprire word o Excel progetto a livello di documento in Visual Studio.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Controllo **riquadro** azioni , assegnare il nome **HelloControl** e fare clic su **Aggiungi**.

    > [!NOTE]
    > In alternativa, è possibile aggiungere **un elemento Controllo** utente al progetto. Le classi generate dagli elementi **Controllo riquadro** azioni e **Controllo utente** sono funzionalmente equivalenti.

4. Dalla scheda **Windows Forms** della Casella degli strumenti **trascinare** un **controllo Button** nel controllo .

    > [!NOTE]
    > Se il controllo non è visibile nella finestra di progettazione, fare doppio clic **su HelloControl** in **Esplora soluzioni**.

5. Aggiungere il codice al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante. L'esempio seguente illustra il codice per un documento Microsoft Office Word.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. In C# è necessario aggiungere un gestore eventi per il clic sul pulsante. È possibile inserire questo codice nel `HelloControl` costruttore dopo la chiamata a `InitializeComponent` .

     Per informazioni su come creare gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office Projects .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Aggiungere il controllo utente al riquadro azioni
 Per visualizzare il riquadro azioni, aggiungere il controllo utente alla proprietà del campo (Word) o del <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` campo `ThisWorkbook.ActionsPane` (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Per aggiungere il controllo utente al riquadro azioni

1. Aggiungere il codice seguente alla classe o come dichiarazione a livello di classe (non aggiungere questo `ThisDocument` codice a un `ThisWorkbook` metodo).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. Aggiungere il codice seguente al gestore eventi della classe o al gestore `ThisDocument_Startup` `ThisDocument` eventi della classe `ThisWorkbook_Startup` `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procedura: Gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
