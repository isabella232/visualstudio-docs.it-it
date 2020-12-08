---
title: 'Procedura: nascondere i controlli nei fogli di foglio durante la stampa'
description: Informazioni sulla possibilità di nascondere i controlli durante la stampa di un foglio di lavoro di Excel Microsoft Office che contiene Windows Forms controlli.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: acc90986dd394e69de12893aac01e0a4f662b1a3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846493"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Procedura: nascondere i controlli nei fogli di foglio durante la stampa
  Quando si stampa un Microsoft Office documento di Excel che contiene controlli Windows Forms, i controlli sono visibili nel foglio di lavoro stampato. È possibile nascondere i controlli quando si stampa un foglio di foglio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Se si nascondono i controlli che visualizzano dati, ad esempio un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , i dati nel controllo non saranno visibili nel foglio di stampa.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Per nascondere i controlli quando viene stampato un foglio di foglio

1. Creare o aprire un progetto di Excel in Visual Studio e verificare che **Sheet1** sia visibile nella finestra di progettazione. Per informazioni sulla creazione di progetti, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dalla scheda **controlli comuni** della **casella degli strumenti** trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.Button> controllo in una cella in `Sheet1` .

3. Nella finestra **Proprietà** impostare la <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> proprietà su **false**.

## <a name="see-also"></a>Vedi anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Cenni preliminari sui controlli Windows Forms nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedura: aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: ridimensionare i controlli all'interno di celle del foglio di comando](../vsto/how-to-resize-controls-within-worksheet-cells.md)
