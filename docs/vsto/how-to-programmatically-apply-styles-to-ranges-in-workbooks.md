---
title: 'Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice'
description: 'Informazioni su come applicare stili denominati alle aree nelle cartelle di lavoro. Excel fornisce alcuni stili predefiniti:'
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 32ba588545d401a7c25f56d5a5f7042d62116a25
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633996"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice
  È possibile applicare stili denominati alle aree nelle cartelle di lavoro. Excel fornisce alcuni stili predefiniti:

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La finestra di dialogo **Formato celle** mostra tutte le opzioni che è possibile usare per formattare le celle e ognuna di queste opzioni è disponibile dal codice. Per visualizzare questa finestra di dialogo in Excel, scegliere **Celle** dal menu **Formato** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Per applicare uno stile a un intervallo denominato in una personalizzazione a livello di documento

1. Creare un nuovo stile e impostare i relativi attributi.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>, assegnargli un testo e quindi applicare il nuovo stile. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Per cancellare uno stile da un intervallo denominato in una personalizzazione a livello di documento

1. Applicare lo stile Normale all'intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Per applicare uno stile a un intervallo denominato in un componente aggiuntivo VSTO

1. Creare un nuovo stile e impostare i relativi attributi.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Creare un oggetto <xref:Microsoft.Office.Interop.Excel.Range>, assegnargli un testo e quindi applicare il nuovo stile.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Per cancellare uno stile da un intervallo denominato in un VSTO componente aggiuntivo

1. Applicare lo stile Normale all'intervallo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
