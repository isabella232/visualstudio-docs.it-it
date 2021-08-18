---
title: Controllo XmlMappedRange
description: Si apprenderà che il controllo XmlMappedRange è un intervallo creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto a una cella in Microsoft Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 173120009b6d295f04c467900e1918361cb5900e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045931"
---
# <a name="xmlmappedrange-control"></a>Controllo XmlMappedRange
  Il controllo è un intervallo creato solo quando viene eseguito il mapping di un elemento dello schema non ripetuto a una <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> cella in Microsoft Office Excel. Ad esempio, quando `maxOccurs` l'attributo di un elemento dello schema è uguale a 1. Dopo Visual Studio l'intervallo mappato XML, è possibile programmarlo direttamente senza dover attraversare il Excel a oggetti. È possibile eliminare un controllo solo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> all'interno Excel quando viene rimosso il mapping degli elementi.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Associare dati al controllo
 Un <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo supporta l'associazione a un singolo campo dati (data binding). Il controllo può supportare data binding e viene creato automaticamente quando viene eseguito il mapping di un elemento dello <xref:Microsoft.Office.Tools.Excel.ListObject> schema ripetuto a una cella. Per altre informazioni, vedere [Controllo ListObject](../vsto/listobject-control.md).

 Il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo è associato a un'origine dati usando la proprietà <xref:System.Windows.Forms.Control.DataBindings%2A> . Quando un oggetto viene aggiunto a una cella del foglio di lavoro, Visual Studio automaticamente un set di dati dai dati nelle celle mappate e associa il controllo a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> tale set di dati. La proprietà data binding predefinita di <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> è <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Se i dati nel set di dati associato vengono aggiornati tramite qualsiasi meccanismo, il <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controllo riflette le modifiche.

## <a name="formatting"></a>Formattazione
 È possibile applicare la stessa formattazione a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> un controllo che è possibile applicare a un oggetto <xref:Microsoft.Office.Interop.Excel.Range> . Questo include i bordi, i tipi di carattere, il formato numero e gli stili.

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

## <a name="see-also"></a>Vedi anche
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Aggiungere controlli XMLMappedRange ai fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: Eseguire il mapping degli schemi ai fogli di lavoro all'interno Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
