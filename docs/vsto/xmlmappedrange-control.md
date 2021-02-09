---
title: Controllo XmlMappedRange
description: Informazioni sul fatto che il controllo XmlMappedRange è un intervallo creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto a una cella in Microsoft Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2849b815c38555be6b149544bb9d9953fe85ec4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894400"
---
# <a name="xmlmappedrange-control"></a>Controllo XmlMappedRange
  Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo è un intervallo creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto su una cella in Microsoft Office Excel. Ad esempio, quando l' `maxOccurs` attributo di un elemento dello schema è uguale a 1. Dopo che Visual Studio ha creato l'intervallo mappato XML, è possibile programmare direttamente su di esso senza dover attraversare il modello a oggetti di Excel. È possibile eliminare un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo all'interno di Excel solo quando viene rimosso il mapping degli elementi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo supporta l'associazione a un singolo campo dati (simple Data Binding). Il <xref:Microsoft.Office.Tools.Excel.ListObject> controllo può supportare data binding complesse e viene creato automaticamente quando viene eseguito il mapping di un elemento dello schema ripetuto su una cella. Per ulteriori informazioni, vedere [controllo ListObject](../vsto/listobject-control.md).

 Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo è associato a un'origine dati utilizzando la <xref:System.Windows.Forms.Control.DataBindings%2A> Proprietà. Quando un oggetto <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene aggiunto a una cella di un foglio di dati, Visual Studio genera automaticamente un set di dati dai dati nelle celle mappate e associa il controllo a tale set di dati. La proprietà data binding predefinita di <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Se i dati nel set di dati associato vengono aggiornati con qualsiasi meccanismo, il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo riflette le modifiche.

## <a name="formatting"></a>Formattazione
 È possibile applicare la stessa formattazione a un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo che è possibile applicare a un <xref:Microsoft.Office.Interop.Excel.Range> . Questo include i bordi, i tipi di carattere, il formato numero e gli stili.

## <a name="events"></a>Eventi
 Gli eventi disponibili per il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo sono i seguenti:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Vedi anche
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: aggiungere controlli XMLMappedRange a fogli di foglio](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: eseguire il mapping di schemi a fogli di fogli di Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
