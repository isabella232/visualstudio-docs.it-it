---
title: 'Procedura: aggiungere controlli XMLMappedRange a fogli di foglio'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544885"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procedura: aggiungere controlli XMLMappedRange a fogli di foglio
  Quando si esegue il mapping di un elemento XML a una cella in Microsoft Office Excel, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo al foglio di lavoro.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo non è disponibile nella **casella degli strumenti** o nella finestra **origini dati** . Non è inoltre possibile creare <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controlli a livello di codice.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Per aggiungere un controllo XMLMappedRange a un foglio di foglio

1. Aprire la cartella di lavoro di Excel nella finestra di progettazione di Visual Studio.

2. Aprire il foglio di controllo in cui si desidera aggiungere il controllo.

3. Nella scheda **Developer** fare clic su **source**.

    > [!NOTE]
    > Se la scheda **Developer** non è visibile sulla barra multifunzione, è necessario abilitarla. Per ulteriori informazioni, vedere [procedura: visualizzare la scheda Developer sulla barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Viene visualizzato il riquadro attività **origine XML** .

4. Nel riquadro attività **origine XML** fare clic su **mappe XML**.

5. Nella finestra di dialogo **mappe XML** fare clic su **Aggiungi**.

     Verrà visualizzata la finestra di dialogo **origine XML** .

6. Selezionare un XML Schema dalla finestra di dialogo **origine XML** e fare clic su **Apri**.

     Lo schema viene aggiunto alla finestra di dialogo **mapping XML** .

7. Nella finestra di dialogo **mappe XML** fare clic su **OK**.

8. Trascinare un elemento dal riquadro attività **origine XML** in una cella del foglio di lavoro.

     Un oggetto <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene creato e aggiunto al progetto.

    > [!NOTE]
    > Se si trascina un elemento padre dal riquadro attività **origine XML** , <xref:Microsoft.Office.Tools.Excel.ListObject> viene creato un controllo.

## <a name="see-also"></a>Vedere anche
- [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
