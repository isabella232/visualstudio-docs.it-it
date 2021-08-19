---
title: 'Procedura: Eseguire un ciclo a livello di codice tra gli elementi trovati nei documenti'
description: Informazioni su come scorrere a livello di codice gli elementi trovati in un documento Microsoft Word usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ab13fee63ab9ed98ba75148a8f099fe1df003bef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083219"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Procedura: Eseguire un ciclo a livello di codice tra gli elementi trovati nei documenti
  Nella classe <xref:Microsoft.Office.Interop.Word.Find> è presente una proprietà <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , che restituisce **true** ogni volta che viene trovato un elemento di cui è stata effettuata la ricerca. Per scorrere in ciclo tutte le istanze trovate in un oggetto <xref:Microsoft.Office.Interop.Word.Range> , è possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Per scorrere in ciclo gli elementi trovati

1. Dichiarare un oggetto <xref:Microsoft.Office.Interop.Word.Range> .

    L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Usare la proprietà <xref:Microsoft.Office.Interop.Word.Find.Found%2A> in un ciclo per ricercare tutte le occorrenze della stringa nel documento e incrementare di un'unità una variabile di tipo Integer ogni volta che viene trovata la stringa.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Visualizza il numero di occorrenze trovate della stringa in una finestra di messaggio.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   Gli esempi seguenti illustrano il metodo completo.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Per scorrere in ciclo gli elementi di una personalizzazione a livello di documento

1. L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Per scorrere in ciclo gli elementi in un VSTO componente aggiuntivo

1. L'esempio seguente mostra il codice completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Cercare e sostituire rext nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Procedura: Impostare le opzioni di ricerca a livello di codice in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
