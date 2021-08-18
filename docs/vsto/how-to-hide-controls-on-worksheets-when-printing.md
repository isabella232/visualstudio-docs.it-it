---
title: 'Procedura: Nascondere i controlli nei fogli di lavoro durante la stampa'
description: Informazioni su come nascondere i controlli durante la stampa di un Microsoft Office Excel di lavoro contenente Windows form.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 621a33d8808b167bc17dd76b265ee0990bb11686
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100036"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Procedura: Nascondere i controlli nei fogli di lavoro durante la stampa
  Quando si stampa un documento Microsoft Office Excel che contiene Windows form, i controlli sono visibili nel foglio di lavoro stampato. È possibile nascondere i controlli durante la stampa di un foglio di lavoro.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Se si nascondono controlli che visualizzano dati, ad esempio , i dati nel controllo non saranno visibili <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> nel foglio di lavoro stampato.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Per nascondere i controlli quando viene stampato un foglio di lavoro

1. Creare o aprire un progetto Excel in Visual Studio e verificare che **Sheet1** sia visibile nella finestra di progettazione. Per informazioni sulla creazione di progetti, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dalla scheda **Controlli comuni** della casella **degli strumenti** trascinare un controllo in una cella <xref:Microsoft.Office.Tools.Excel.Controls.Button> in `Sheet1` .

3. Nella finestra **Proprietà** impostare la <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> proprietà su **False**.

## <a name="see-also"></a>Vedi anche
- [Controlli su Office documenti](../vsto/controls-on-office-documents.md)
- [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Procedura: Aggiungere controlli form Windows a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)
