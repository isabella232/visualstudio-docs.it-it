---
title: "Procedura: aggiungere un riquadro attività personalizzato a un'applicazione"
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0df4d51795f01c98790f1d5b0525c45cc71899ab
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546211"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Procedura: aggiungere un riquadro attività personalizzato a un'applicazione
  È possibile aggiungere un riquadro attività personalizzato alle applicazioni elencate sopra usando un componente aggiuntivo VSTO. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Aggiungere un riquadro attività personalizzato a un'applicazione

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Per aggiungere un riquadro attività personalizzato a un'applicazione

1. Aprire o creare un progetto di componente aggiuntivo VSTO per una delle applicazioni elencate sopra. Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del nuovo controllo utente in **UserControl**, quindi fare clic su **Aggiungi**.

     Il controllo utente viene visualizzato nella finestra di progettazione.

4. Aggiungere uno o più controlli Windows Forms dalla **casella degli strumenti** al controllo utente.

5. Aprire il file di codice **ThisAddIn.cs** o **ThisAddIn. vb** .

6. Aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn` .

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup`. Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes` . Il codice visualizza anche il riquadro attività.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Questo codice associa il riquadro attività alla finestra attiva nell'applicazione. Per alcune applicazioni, si potrebbe voler modificare il codice perché il riquadro attività venga visualizzato con altri documenti o elementi nell'applicazione. Per ulteriori informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vedere anche
- [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Procedura dettagliata: automatizzare un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
