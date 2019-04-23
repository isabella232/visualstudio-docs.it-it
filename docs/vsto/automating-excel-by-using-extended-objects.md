---
title: Automazione di Excel usando oggetti estesi
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8a08b58871652cea6332f4239e9da98b28f28e0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070056"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automazione di Excel usando oggetti estesi
  Quando si sviluppano soluzioni Excel in Visual Studio, è possibile usare *elementi host* e *controlli host*nelle soluzioni. Si tratta di oggetti che estendono determinati oggetti usati comunemente nel modello a oggetti di Excel (cioè, il modello a oggetti esposto dall'assembly di interoperabilità primario per Excel), come ad esempio gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range> . Gli oggetti estesi si comportano come gli oggetti di Excel sui quali si basano, ma forniscono funzionalità aggiuntive come ad esempio nuovi eventi e funzionalità di data binding agli oggetti.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Gli elementi e i controlli host sono disponibili nelle personalizzazioni a livello di documento e dei componenti aggiuntivi VSTO, sebbene il contenuto in cui possono essere usati è diverso per ogni tipo di soluzione. Per altre informazioni, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Elementi host di Excel
 I progetti Excel consentono l'accesso a diversi elementi host:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Questo elemento host contiene e rappresenta un foglio di lavoro nel progetto. Viene anche usato come contenitore per controlli gestiti, inclusi i controlli host e quelli Windows Form e gestisce informazioni relative ai controlli della relativa area. Per altre informazioni, vedere [elemento host Worksheet](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Questo elemento host rappresenta la cartella di lavoro del progetto e viene usato come contenitore per i componenti condivisi da tutti i fogli di lavoro nella cartella di lavoro. Per altre informazioni, vedere [elemento host Workbook](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Questo elemento host è un foglio di lavoro in Excel che contiene solo un grafico ed espone eventi.

     Quando si aggiunge un foglio grafico in fase di progettazione come nuovo foglio nel progetto di personalizzazione a livello di documento di Microsoft Office Excel, Visual Studio crea automaticamente un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet> .

     Sebbene un elemento host <xref:Microsoft.Office.Tools.Excel.ChartSheet> sia un foglio di lavoro in Excel, non è possibile aggiungere alcun controllo al foglio grafico. Se si vuole disporre di altri controlli in un foglio di lavoro con un grafico, non usare un foglio grafico. Al contrario, è possibile usare un grafico come oggetto incorporato in un foglio di lavoro usando il controllo host <xref:Microsoft.Office.Tools.Excel.Chart> . Per altre informazioni, vedere [controllo del grafico](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>controlli host di Excel
 Vi sono vari controlli per Excel che consentono di creare, organizzare e automatizzare le cartelle e i fogli di lavoro. Si tratta di controlli host che forniscono funzionalità di data binding ed eventi che non sono disponibili nelle rispettive controparti del modello a oggetti di Excel nativo.

 Per altre informazioni sui controlli host da poter usare in progetti Excel, vedere i seguenti argomenti:

- [Controllo Chart](../vsto/chart-control.md)

- [ListObject (controllo)](../vsto/listobject-control.md)

- [NamedRange (controllo)](../vsto/namedrange-control.md)

- [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Vedere anche
- [Procedura: Riempire controlli ListObject con dati](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Procedura: Aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Procedura: Aggiungere controlli XMLMappedRange a fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Procedura: Convalidare i dati quando viene aggiunta una nuova riga a un controllo ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Procedura: Eseguire il mapping delle colonne ListObject ai dati](../vsto/how-to-map-listobject-columns-to-data.md)
- [Procedura dettagliata: Programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
