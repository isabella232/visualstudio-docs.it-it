---
title: Aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel
description: Per informazioni su come aggiungere un riquadro azioni a un documento Microsoft Office Word o a una cartella di lavoro di Microsoft Excel, è innanzitutto necessario creare un controllo utente Windows Form.
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
ms.workload:
- office
ms.openlocfilehash: f9488a15f851446c5779bdb1a4572e69a1cf3053
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917527"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel
  Per aggiungere un riquadro azioni a un documento Microsoft Office Word o a una cartella di lavoro di Microsoft Excel, creare prima un controllo utente Windows Form. Aggiungere quindi il controllo utente alla <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o del `ThisWorkbook.ActionsPane` campo (Excel) nel progetto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Creazione del controllo utente
 Nella procedura seguente viene illustrato come creare un controllo utente in un progetto di Word o di Excel. Aggiunge anche un pulsante al controllo utente che scrive il testo nel documento o nella cartella di lavoro quando viene selezionato.

#### <a name="to-create-the-user-control"></a>Per creare il controllo utente

1. Aprire il progetto a livello di documento di Word o Excel in Visual Studio.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il **controllo riquadro azioni**, denominarlo **HelloControl** e fare clic su **Aggiungi**.

    > [!NOTE]
    > In alternativa, è possibile aggiungere un elemento di **controllo utente** al progetto. Le classi generate dal **controllo del riquadro azioni** e dagli elementi del **controllo utente** sono funzionalmente equivalenti.

4. Dalla scheda **Windows Form** della **casella degli strumenti** trascinare un controllo **Button** sul controllo.

    > [!NOTE]
    > Se il controllo non è visibile nella finestra di progettazione, fare doppio clic su **HelloControl** in **Esplora soluzioni**.

5. Aggiungere il codice al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante. Nell'esempio seguente viene illustrato il codice per un documento di Word Microsoft Office.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. In C# è necessario aggiungere un gestore eventi per il clic sul pulsante. È possibile inserire questo codice nel `HelloControl` Costruttore dopo la chiamata a `InitializeComponent` .

     Per informazioni su come creare i gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Aggiungere il controllo utente al riquadro azioni
 Per visualizzare il riquadro azioni, aggiungere il controllo utente alla <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o del `ThisWorkbook.ActionsPane` campo (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Per aggiungere il controllo utente al riquadro azioni

1. Aggiungere il codice seguente alla `ThisDocument` classe o `ThisWorkbook` come dichiarazione a livello di classe (non aggiungere questo codice a un metodo).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Aggiungere il codice seguente al `ThisDocument_Startup` gestore eventi della `ThisDocument` classe o del `ThisWorkbook_Startup` gestore eventi della `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procedura: gestire il layout di controllo nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
