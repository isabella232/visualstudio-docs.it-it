---
title: 'Procedura: Nascondere controlli nei fogli di lavoro durante la stampa'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac1145f27cf9fcf5746a18a88f1cc7bc901e38fa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875797"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Procedura: Nascondere controlli nei fogli di lavoro durante la stampa
  Quando si stampa un documento di Microsoft Office Excel che contiene controlli Windows Form, i controlli sono visibili nel foglio di lavoro. È possibile nascondere i controlli quando si stampa un foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Se si nascondono i controlli che visualizzano i dati, ad esempio un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, i dati nel controllo non saranno visibili nel foglio di lavoro.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Per nascondere i controlli in quando un foglio di lavoro viene stampato  
  
1.  Creare o aprire un progetto di Excel in Visual Studio e verificare che **Sheet1** è visibile nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [come: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.Button> control a una cella per `Sheet1`.  
  
3.  Nel **le proprietà** impostare nella finestra di <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> proprietà **False**.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controlli Windows Form in panoramica di documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
