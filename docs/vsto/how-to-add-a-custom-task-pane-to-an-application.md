---
title: "Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 24053fcc8918b80e05031739c36059e82ea024a7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874393"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione
  È possibile aggiungere un riquadro attività personalizzato alle applicazioni elencate sopra usando un componente aggiuntivo VSTO. Per altre informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Aggiungere un riquadro attività personalizzato a un'applicazione  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Per aggiungere un riquadro attività personalizzato a un'applicazione  
  
1.  Aprire o creare un progetto di componente aggiuntivo VSTO per una delle applicazioni elencate sopra. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo, modificare il nome del nuovo controllo utente per **MyUserControl**, quindi fare clic su **Aggiungi**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
4.  Aggiungere uno o più controlli Windows Form dal **casella degli strumenti** al controllo utente.  
  
5.  Aprire il **ThisAddIn.cs** oppure **ThisAddIn. vb** file di codice.  
  
6.  Aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn` .  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup`. Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes` . Il codice visualizza anche il riquadro attività.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Questo codice associa il riquadro attività alla finestra attiva nell'applicazione. Per alcune applicazioni, si potrebbe voler modificare il codice perché il riquadro attività venga visualizzato con altri documenti o elementi nell'applicazione. Per altre informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
