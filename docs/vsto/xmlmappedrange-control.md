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
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985365"
---
# <a name="xmlmappedrange-control"></a>Controllo XmlMappedRange
  Il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è un intervallo creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto su una cella in Microsoft Office Excel. Ad esempio, quando l'attributo `maxOccurs` di un elemento dello schema è uguale a 1. Dopo che Visual Studio ha creato l'intervallo mappato XML, è possibile programmare direttamente su di esso senza dover attraversare il modello a oggetti di Excel. È possibile eliminare un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> in Excel solo quando viene rimosso il mapping degli elementi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> supporta l'associazione a un singolo campo dati (data binding semplice). Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> può supportare data binding complessi e viene creato automaticamente quando viene eseguito il mapping di un elemento dello schema ripetuto su una cella. Per ulteriori informazioni, vedere [controllo ListObject](../vsto/listobject-control.md).

 Il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è associato a un'origine dati utilizzando la proprietà <xref:System.Windows.Forms.Control.DataBindings%2A>. Quando un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene aggiunto a una cella di un foglio di controllo, Visual Studio genera automaticamente un set di dati dai dati nelle celle mappate e associa il controllo a tale set di dati. Viene <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>la proprietà data binding predefinita del <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>.

 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> riflette le modifiche.

## <a name="formatting"></a>Formattazione
 È possibile applicare la stessa formattazione a un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> che è possibile applicare a una <xref:Microsoft.Office.Interop.Excel.Range>. Questo include i bordi, i tipi di carattere, il formato numero e gli stili.

## <a name="events"></a>eventi
 Gli eventi disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> sono:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Vedere anche
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: aggiungere controlli XMLMappedRange a fogli di foglio](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
