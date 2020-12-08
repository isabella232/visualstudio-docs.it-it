---
title: 'Procedura: gestire il layout di controllo nei riquadri azioni'
description: Informazioni su come gestire il layout dei controlli nei riquadri azioni scrivendo codice per creare correttamente lo stack dei controlli utente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbee49a97ab6cb3e6084950e53f30b3cb6ce1b7c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848248"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procedura: gestire il layout di controllo nei riquadri azioni
  Per impostazione predefinita, un riquadro azioni è ancorato a destra di un documento o di un foglio di foglio. Tuttavia, può essere ancorato a sinistra, in alto o in basso. Se si usano più controlli utente, è possibile scrivere codice per lo stack corretto dei controlli utente nel riquadro azioni. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 L'ordine dello stack dei controlli dipende dal fatto che il riquadro azioni sia ancorato verticalmente o orizzontalmente.

> [!NOTE]
> Se l'utente ridimensiona il riquadro azioni in fase di esecuzione, è possibile impostare i controlli per il ridimensionamento con il riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. Per altre informazioni, vedere [How to: Anchor Controls on Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Per impostare l'ordine dello stack dei controlli del riquadro azioni

1. Aprire un progetto a livello di documento per Microsoft Office parola che include un riquadro azioni con più controlli utente o controlli riquadro azioni nidificate. Per altre informazioni, vedere [procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. Fare clic con il pulsante destro del mouse su **ThisDocument.cs** o **ThisDocument. vb** in **Esplora soluzioni** , quindi scegliere **Visualizza codice**.

3. Nel <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> gestore eventi del riquadro azioni, controllare se l'orientamento del riquadro azioni è orizzontale.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Se l'orientamento è orizzontale, sovrapporre i controlli del riquadro azioni a sinistra; in caso contrario, impilarli dalla parte superiore.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. In C# è necessario aggiungere un gestore eventi per al `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento. Per informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Eseguire il progetto e verificare che i controlli del riquadro azioni siano impilati da sinistra a destra quando il riquadro azioni è ancorato alla parte superiore del documento e i controlli sono impilati dall'alto verso il basso quando il riquadro azioni è ancorato a destra del documento.

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Un progetto a livello di documento di Word con un riquadro azioni che contiene più controlli utente o controlli riquadro azioni nidificate.

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procedura dettagliata: inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
