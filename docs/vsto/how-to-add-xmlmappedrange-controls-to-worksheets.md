---
title: 'Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6f055ba84c4e6a6b48c13f3eef9a433eb4c5b3e1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605848"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro
  Quando si esegue il mapping di un elemento XML a una cella in Microsoft Office Excel, Visual Studio aggiunge automaticamente un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo al foglio di lavoro.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
>  Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo non è disponibile nel **casella degli strumenti** o il **Zdroje dat** finestra. Inoltre, non è possibile creare <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controlla a livello di codice.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Per aggiungere un controllo XMLMappedRange a un foglio di lavoro

1.  Aprire la cartella di lavoro di Excel nella finestra di progettazione di Visual Studio.

2.  Aprire il foglio di lavoro in cui si desidera aggiungere il controllo.

3.  Nel **sviluppatore** scheda, fare clic su **origine**.

    > [!NOTE]
    >  Se il **sviluppatore** scheda non è visibile sulla barra multifunzione, è necessario abilitarla. Per altre informazioni, vedere [Procedura: Visualizzare la scheda sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Il **origine XML** viene visualizzato il riquadro attività.

4.  Nel **origine XML** del riquadro attività, fare clic su **XML Maps**.

5.  Nel **XML Maps** della finestra di dialogo fare clic su **Add**.

     Il **origine XML** verrà visualizzata la finestra di dialogo.

6.  Selezionare uno schema XML dal **origine XML** finestra di dialogo e fare clic su **Open**.

     Lo schema viene aggiunto per il **esegue il mapping XML** nella finestra di dialogo.

7.  Nel **XML Maps** finestra di dialogo, fare clic su **OK**.

8.  Trascinare un elemento dal **origine XML** riquadro attività a una cella del foglio di lavoro.

     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene creato e aggiunto al progetto.

    > [!NOTE]
    >  Se si trascina un elemento padre di **origine XML** riquadro attività, un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo viene creato.

## <a name="see-also"></a>Vedere anche
- [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
