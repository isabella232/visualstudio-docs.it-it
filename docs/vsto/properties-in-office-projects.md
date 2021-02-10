---
title: Proprietà nei progetti di Office
description: Informazioni sulle proprietà disponibili per i progetti di Office in Visual Studio tramite il Finestra Proprietà.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f7a2ab04e1926a53c3d3aa05023103206c6aa01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971765"
---
# <a name="properties-in-office-projects"></a>Proprietà nei progetti di Office
  Per i progetti di Office in Visual Studio, sono disponibili numerose proprietà importanti, alle quali è possibile accedere dalla finestra **Proprietà** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Spazio dei nomi per elemento host
 Utilizzare la proprietà **spazio dei nomi per elemento host** per modificare lo spazio dei nomi per le classi di elementi host (ad esempio, le `ThisAddIn` `ThisWorkbook` classi, o `ThisDocument` ) nei progetti Visual C#. Questa proprietà viene visualizzata nella finestra **Proprietà** quando si seleziona il nodo del documento in un progetto a livello di documento, ad esempio *ExcelWorkbook1.xlsx* o *WordDocument1.docx*, o il nodo dell'applicazione in un progetto di componente aggiuntivo VSTO, ad esempio Excel o Word, in **Esplora soluzioni**.

 Quando si crea un progetto di Office in Visual C#, agli elementi host viene attribuito uno spazio dei nomi in base al nome del progetto. Si consiglia di usare la proprietà **Spazio dei nomi per elemento host** per modificare lo spazio dei nomi anziché modificare direttamente i file di codice. Quando si usa questa proprietà, lo spazio dei nomi viene modificato nei file di codice (nascosti) generati, oltre che nei file di codice visibili.

## <a name="cacheindocument"></a>CacheInDocument
 La proprietà **CacheInDocument** viene visualizzata nella finestra **Proprietà** per i progetti a livello di documento quando si seleziona un'istanza di un oggetto <xref:System.Data.DataSet> nella finestra di progettazione di Visual Studio. È possibile memorizzare nella cache solo i membri pubblici. Assicurarsi che la proprietà **Modificatori** sia impostata su **Pubblica** se si desidera memorizzare nella cache un oggetto <xref:System.Data.DataSet>.

 Questa proprietà accetta un valore booleano:

- Selezionare **true** per memorizzare nella cache il set di dati nel documento.

- Selezionare **false** se non si desidera che il set di dati venga memorizzato nella cache del documento.

  Per ulteriori informazioni sulla memorizzazione nella cache dei dati, vedere la pagina relativa [ai dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Value2
 La proprietà **Value2** è disponibile solo per progetti modello o cartella di lavoro di Excel. Viene visualizzata nel nodo proprietà **Databindings** nella finestra **Proprietà** quando si seleziona un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella finestra di progettazione del foglio di lavoro.

 Usare la proprietà **Value2** nella finestra **Proprietà** per associare la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> di <xref:Microsoft.Office.Tools.Excel.NamedRange> a un campo dell'origine dati.

## <a name="see-also"></a>Vedi anche
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Panoramica sui modelli di progetto di Office](../vsto/office-project-templates-overview.md)
- [Eventi nei progetti di Office](../vsto/events-in-office-projects.md)
