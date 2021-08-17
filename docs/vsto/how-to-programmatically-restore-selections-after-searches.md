---
title: 'Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche'
description: Informazioni su come usare Visual Studio per ripristinare le selezioni a livello di codice dopo le ricerche in un Microsoft Word documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 57f71cad1335c29f4e92bb760de251f6100f51a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026174"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche
  Se si trova e si sostituisce testo in un documento, è possibile ripristinare la selezione originale dell'utente al termine della ricerca.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Il codice nella procedura di esempio usa due <xref:Microsoft.Office.Interop.Word.Range> oggetti . Uno archivia l'oggetto <xref:Microsoft.Office.Interop.Word.Selection> corrente e uno imposta l'intero documento da usare come intervallo di ricerca.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Per ripristinare la selezione originale dell'utente dopo una ricerca

1. Creare gli <xref:Microsoft.Office.Interop.Word.Range> oggetti per il documento e la selezione corrente.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet83":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet83":::

2. Eseguire l'operazione di ricerca e sostituzione.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet84":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet84":::

3. Selezionare l'intervallo iniziale per ripristinare la selezione originale dell'utente.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet85":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet85":::

   L'esempio seguente mostra il metodo completo.

## <a name="example"></a>Esempio
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet82":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet82":::

## <a name="see-also"></a>Vedere anche
- [Procedura: Cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: Impostare le opzioni di ricerca a livello di codice in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Procedura: Eseguire un ciclo a livello di codice tra gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
