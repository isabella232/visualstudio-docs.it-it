---
title: 'Procedura: Salvare documenti Visio codice'
description: Informazioni su come usare Visual Studio salvare a livello di codice microsoft Visio documenti esistenti e nuovi documenti che non sono ancora stati salvati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7deb727e956adb9e7ba80a083f774aaca9b5b864
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026148"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Procedura: Salvare documenti Visio codice
  Esistono varie modalità per salvare documenti di Microsoft Office Visio:

- Salvare le modifiche in un documento esistente.

- Salvare un nuovo documento oppure salvare un documento con un nuovo nome.

- Salvare un documento con gli argomenti specificati.

  Per altre informazioni, vedere la documentazione di riferimento di VBA per i metodi [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) e [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .

## <a name="save-an-existing-document"></a>Salvare un documento esistente

### <a name="to-save-a-document"></a>Per salvare un documento

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.Save` della classe `Microsoft.Office.Tools.Visio.Document` di un documento salvato in precedenza.

     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

    > [!NOTE]
    > Il metodo `Microsoft.Office.Interop.Visio.Document.Save` genera un'eccezione se non è stato ancora salvato un nuovo documento di Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet11":::

## <a name="save-a-document-with-a-new-name"></a>Salvare un documento con un nuovo nome
 Usare il metodo `Microsoft.Office.Interop.Visio.Document.SaveAs` per salvare un nuovo documento oppure un documento che ha un nuovo nome. Con questo metodo è necessario specificare il nuovo nome del file.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Per salvare il documento attivo con un nuovo nome

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.SaveAs` di `Microsoft.Office.Tools.Visio.Document` che si vuole salvare usando un percorso completo che include un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.

     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet10":::

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Salvare un documento con un nuovo nome e argomenti specificati
 Usare il metodo `Microsoft.Office.Interop.Visio.Document.SaveAsEx` per salvare un documento con un nuovo nome e specificare qualsiasi argomento applicabile da applicare al documento.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Per salvare un documento con un nuovo nome e argomenti specificati

- Chiamare il metodo `Microsoft.Office.Interop.Visio.Document.SaveAsEx` di `Microsoft.Office.Tools.Visio.Document` che si vuole salvare usando un percorso completo che include un nome file. Se un file con quel nome già esiste in quella cartella, viene generata un'eccezione.

     L'esempio di codice seguente salva il documento attivo con un nuovo nome, lo contrassegna come di sola lettura e visualizza il documento nell'elenco di documenti Usati di recente. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presenta i requisiti seguenti:

- Per salvare un documento con un nuovo nome, una directory denominata deve trovarsi nella cartella Documenti (per Windows XP e versioni precedenti) o nella cartella Documenti `Test` (per Windows  Vista). 

## <a name="see-also"></a>Vedi anche
- [Visio soluzioni](../vsto/visio-solutions.md)
- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)
- [Procedura: Creare nuovi documenti Visio codice](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Procedura: Aprire documenti Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)
- [Procedura: Chiudere documenti Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)
- [Procedura: Stampare documenti Visio codice](../vsto/how-to-programmatically-print-visio-documents.md)
