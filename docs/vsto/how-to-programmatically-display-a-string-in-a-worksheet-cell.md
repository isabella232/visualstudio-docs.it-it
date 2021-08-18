---
title: 'Procedura: Visualizzare una stringa in una cella del foglio di lavoro a livello di codice'
description: Informazioni su come visualizzare a livello di codice una stringa in una cella Microsoft Excel foglio di lavoro usando un controllo NamedRange o un oggetto intervallo Excel nativo.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5058a41a40ed834dc715a09de3b28c0e28cf594a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099802"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Procedura: Visualizzare una stringa in una cella del foglio di lavoro a livello di codice
  In questo esempio viene illustrato come visualizzare il testo in una cella a livello di codice. Per visualizzare il testo nella cella, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 In questo esempio viene utilizzato <xref:Microsoft.Office.Tools.Excel.NamedRange> un controllo denominato `message` . Il controllo deve essere aggiunto a una personalizzazione a livello di documento in fase di progettazione. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe .

### <a name="to-display-text-in-a-namedrange-control"></a>Per visualizzare testo in un controllo NamedRange

1. Impostare il valore del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo su **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Usare un intervallo Excel nativo
 Il codice seguente crea un nuovo intervallo a livello di codice e quindi assegna un valore a esso.

### <a name="to-display-text-in-an-excel-range"></a>Per visualizzare il testo in un intervallo Excel dati

1. Recuperare l'intervallo in **corrispondenza della cella A1** `Sheet1` in e impostare il valore su **Hello World**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Raccogliere dati usando un modulo Windows dati](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Risolvere i problemi Office soluzioni](../vsto/troubleshooting-office-solutions.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Accesso globale agli oggetti nei Office progetto](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
