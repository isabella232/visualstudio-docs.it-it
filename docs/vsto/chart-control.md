---
title: Controllo Grafico
description: Si apprenderà che quando si aggiunge un grafico a un foglio Visual Studio crea un oggetto grafico su cui è possibile programmare direttamente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 957f9a8a1959879f32e3eb4ee9b75645308d7ea6b57358ec37e04e9ea433f42c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226409"
---
# <a name="chart-control"></a>Controllo Grafico
  Il controllo <xref:Microsoft.Office.Tools.Excel.Chart> è un oggetto grafico che espone eventi. Quando si aggiunge un grafico a un foglio di lavoro, Visual Studio crea un oggetto <xref:Microsoft.Office.Tools.Excel.Chart> su cui è possibile programmare direttamente senza dover passare attraverso il modello a oggetti di Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Creare il controllo
 È possibile aggiungere controlli a un foglio Microsoft Office Excel in fase di progettazione o in fase di <xref:Microsoft.Office.Tools.Excel.Chart> esecuzione in un progetto a livello di documento.

 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.Chart> a un foglio di lavoro in fase di esecuzione in un componente aggiuntivo VSTO. Per altre informazioni, vedere [Procedura: Aggiungere controlli Chart ai fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Gli oggetti grafico creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [Aggiungere controlli Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="formatting"></a>Formattazione
 Tutta la formattazione che può essere applicata a un oggetto <xref:Microsoft.Office.Interop.Excel.Chart> può essere applicata anche a un controllo <xref:Microsoft.Office.Tools.Excel.Chart>. Sono inclusi bordi, tipi di carattere, tipo di grafico, griglie, legenda ed etichette dati.

## <a name="events"></a>Eventi
 Gli eventi seguenti sono disponibili per il controllo <xref:Microsoft.Office.Tools.Excel.Chart> :

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Vedi anche
- [Office esempi di sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md)
- [Estendere documenti di Word Excel cartelle di lavoro in VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli sui Office di lavoro](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli per Office documenti in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Procedura: Aggiungere controlli Chart ai fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
