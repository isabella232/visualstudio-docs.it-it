---
title: 'Procedura: Elencare a livello di codice i file delle cartelle di lavoro usati di recente'
description: Informazioni su come elencare i file delle cartelle di lavoro usati di Microsoft Excel a livello di codice usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e9652a60149a068643a4a8d0b06728534a4ac521
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710065"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: Elencare a livello di codice i file delle cartelle di lavoro usati di recente
  La proprietà restituisce una raccolta che contiene i nomi di tutti i file visualizzati nell'elenco Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> di file usati di recente. La lunghezza dell'elenco varia a seconda del numero di file che l'utente ha selezionato per la conservazione. È possibile visualizzare i risultati in un intervallo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per elencare le cartelle di lavoro usate di recente in un oggetto intervallo

1. Scorrere l'elenco dei file recenti e visualizzare i nomi nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
