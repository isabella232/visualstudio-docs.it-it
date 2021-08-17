---
title: 'Procedura: Aggiungere controlli XMLMappedRange ai fogli di lavoro'
description: Si apprenderà che quando si esegue il mapping di un elemento XML a una cella in Microsoft Office Excel, Visual Studio aggiunge automaticamente un controllo XmlMappedRange al foglio di lavoro.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8fa5b3037b29cf15537215c9bf623c57ac8a119d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106328"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Procedura: Aggiungere controlli XMLMappedRange ai fogli di lavoro
  Quando si esegue il mapping di un elemento XML a una cella Microsoft Office Excel, Visual Studio aggiunge <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> automaticamente un controllo al foglio di lavoro.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo non è disponibile nella casella degli **strumenti** o nella **finestra Origini** dati. Inoltre, non è possibile creare controlli <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a livello di codice.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Per aggiungere un controllo XMLMappedRange a un foglio di lavoro

1. Aprire la Excel di lavoro di nella Visual Studio predefinita.

2. Aprire il foglio di lavoro in cui si vuole aggiungere il controllo.

3. Nella scheda **Sviluppatore** fare clic su **Origine.**

    > [!NOTE]
    > Se la **scheda Sviluppatore** non è visibile sulla barra multifunzione, è necessario abilitarla. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

     Verrà **visualizzato il riquadro** attività Origine XML .

4. Nel riquadro **attività Origine XML** fare clic su XML **Mappe**.

5. Nella finestra **di dialogo Mappe** xml fare clic su **Aggiungi**.

     Verrà **visualizzata la finestra di** dialogo Origine XML .

6. Selezionare uno schema XML nella finestra **di dialogo Origine XML e** fare clic su **Apri**.

     Lo schema viene aggiunto alla finestra **di Mappe** XML.

7. Nella finestra **di dialogo Mappe** XML fare clic su **OK.**

8. Trascinare un elemento dal **riquadro attività Origine XML** in una cella del foglio di lavoro.

     Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> oggetto viene creato e aggiunto al progetto.

    > [!NOTE]
    > Se si trascina un elemento padre dal **riquadro attività Origine XML,** viene <xref:Microsoft.Office.Tools.Excel.ListObject> creato un controllo .

## <a name="see-also"></a>Vedi anche
- [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
