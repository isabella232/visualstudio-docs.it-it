---
title: 'Procedura: Gestire il layout dei controlli nei riquadri azioni'
description: Informazioni su come gestire il layout dei controlli nei riquadri azioni scrivendo codice per impilare correttamente i controlli utente.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3759bb07c7dc4ec0548b8178ee561190c410180e34e531463c472a82cf67f3e2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351876"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procedura: Gestire il layout dei controlli nei riquadri azioni
  Un riquadro azioni è ancorato a destra di un documento o di un foglio di lavoro per impostazione predefinita. tuttavia, può essere ancorato a sinistra, in alto o in basso. Se si usano più controlli utente, è possibile scrivere codice per impilare correttamente i controlli utente nel riquadro azioni. Per altre informazioni, vedere [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 L'ordine dello stack dei controlli dipende dal fatto che il riquadro azioni sia ancorato verticalmente o orizzontalmente.

> [!NOTE]
> Se l'utente ridimensiona il riquadro azioni in fase di esecuzione, è possibile impostare i controlli per il ridimensionamento con il riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. Per altre informazioni, vedere [Procedura: Ancorare i](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)controlli Windows Form.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Per impostare l'ordine dello stack dei controlli del riquadro azioni

1. Aprire un progetto a livello di documento per Microsoft Office Word che include un riquadro azioni con più controlli utente o controlli riquadro azioni annidati. Per altre informazioni, vedere Procedura: Aggiungere un riquadro azioni a documenti di [Word o Excel cartelle di lavoro.](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

2. Fare clic con il pulsante destro del mouse su **ThisDocument.cs** **o ThisDocument.vb** **in** Esplora soluzioni quindi scegliere **Visualizza codice**.

3. Nel gestore eventi del riquadro azioni verificare se l'orientamento del riquadro azioni <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> è orizzontale.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet30":::

4. Se l'orientamento è orizzontale, impilare i controlli del riquadro azioni da sinistra; In caso contrario, impilarli dall'alto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet31":::

5. In C# è necessario aggiungere un gestore eventi per `ActionsPane` l'oggetto al <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore eventi. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet32":::

6. Eseguire il progetto e verificare che i controlli del riquadro azioni siano impilati da sinistra a destra quando il riquadro azioni è ancorato nella parte superiore del documento e che i controlli siano impilati dall'alto verso il basso quando il riquadro azioni è ancorato sul lato destro del documento.

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet29":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet29":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Progetto a livello di documento di Word con un riquadro azioni che contiene più controlli utente o controlli riquadro azioni annidati.

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
