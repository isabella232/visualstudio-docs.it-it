---
title: Controllo XmlMappedRange
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cde5489d970de02afbce28ab9c60c677ab199c84
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105682"
---
# <a name="xmlmappedrange-control"></a>Controllo XmlMappedRange
  Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo è un intervallo che viene creato solo quando un elemento dello schema non ripetuto viene eseguito il mapping a una cella in Microsoft Office Excel. Ad esempio, quando il `maxOccurs` attributo di un elemento dello schema è uguale a 1. Dopo che Visual Studio crea l'intervallo mappato XML, è possibile programmare contrastarla direttamente senza dover passare attraverso il modello a oggetti Excel. È possibile eliminare solo un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo all'interno di Excel quando viene rimosso il mapping dell'elemento.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Usare il mapping XML in Excel? ](http://go.microsoft.com/fwlink/?LinkID=130288).

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo supporta l'associazione a un singolo campo di dati (data binding semplice). Il <xref:Microsoft.Office.Tools.Excel.ListObject> può controllo supporta l'associazione di dati complessi e viene creato automaticamente quando un elemento ripetuto dello schema è mappato a una cella. Per altre informazioni, vedere [ListObject control](../vsto/listobject-control.md).

 Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è associato a un'origine dati usando il <xref:System.Windows.Forms.Control.DataBindings%2A> proprietà. Quando un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene aggiunto a una cella di foglio di lavoro, Visual Studio genera automaticamente un set di dati dai dati delle celle mappate e associa il controllo di set di dati. La proprietà di associazione di dati predefinito di <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo riflette le modifiche.

## <a name="formatting"></a>Formattazione
 È possibile applicare la stessa formattazione a un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo che è possibile applicare a un <xref:Microsoft.Office.Interop.Excel.Range>. Questo include i bordi, i tipi di carattere, il formato numero e gli stili.

## <a name="events"></a>Eventi
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo sono:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Vedere anche
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: Mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
