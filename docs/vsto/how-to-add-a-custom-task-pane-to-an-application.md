---
title: "Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione"
description: Informazioni su come aggiungere un riquadro attività personalizzato alle applicazioni usando il componente aggiuntivo Visual Studio Tools per Office (VSTO).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3477930ba181f4a0f33d8711e882cda8ba63af17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026369"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Procedura: Aggiungere un riquadro attività personalizzato a un'applicazione
  È possibile aggiungere un riquadro attività personalizzato alle applicazioni elencate sopra usando un componente aggiuntivo VSTO. Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="add-a-custom-task-pane-to-an-application"></a>Aggiungere un riquadro attività personalizzato a un'applicazione

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Per aggiungere un riquadro attività personalizzato a un'applicazione

1. Aprire o creare un progetto di componente aggiuntivo VSTO per una delle applicazioni elencate sopra. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.

3. Nella finestra **di dialogo Aggiungi nuovo** elemento modificare il nome del nuovo controllo utente in **MyUserControl** e quindi fare clic su **Aggiungi**.

     Il controllo utente viene visualizzato nella finestra di progettazione.

4. Aggiungere uno o più Windows Form dalla casella **degli** strumenti al controllo utente.

5. Aprire il file **di codice ThisAddIn.cs** **o ThisAddIn.vb.**

6. Aggiungere il codice seguente alla classe `ThisAddIn` . Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup`. Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes` . Il codice visualizza anche il riquadro attività.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Questo codice associa il riquadro attività alla finestra attiva nell'applicazione. Per alcune applicazioni, si potrebbe voler modificare il codice perché il riquadro attività venga visualizzato con altri documenti o elementi nell'applicazione. Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Vedi anche
- [Office Personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md)
- [Riquadri attività personalizzati](../vsto/custom-task-panes.md)
- [Procedura dettagliata: Automatizzare un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
