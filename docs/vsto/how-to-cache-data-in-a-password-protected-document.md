---
title: 'Procedura: memorizzare nella cache i dati in un documento protetto da password'
description: Si apprenderà che se si aggiungono dati alla cache dei dati in un documento o in una cartella di lavoro protetta con una password, è possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a11b70da4bdd2500f70d2b45f025340af21ea94
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845999"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procedura: memorizzare nella cache i dati in un documento protetto da password
  Se si aggiungono dati alla cache dei dati in un documento o in una cartella di lavoro protetta con una password, le modifiche apportate ai dati memorizzati nella cache non vengono salvate automaticamente. È possibile salvare le modifiche apportate ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Memorizzazione nella cache nei documenti di Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Per memorizzare nella cache i dati in un documento di Word protetto con una password

1. Nella `ThisDocument` classe contrassegnare un campo o una proprietà pubblica da memorizzare nella cache. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

2. Eseguire l'override del <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo nella `ThisDocument` classe e rimuovere la protezione dal documento.

     Quando il documento viene salvato, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per offrire la possibilità di rimuovere la protezione del documento. Questo consente di salvare le modifiche apportate ai dati memorizzati nella cache.

3. Eseguire l'override del <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo nella `ThisDocument` classe e riapplicare la protezione al documento.

     Una volta salvato il documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per offrire l'opportunità di riapplicare la protezione al documento.

### <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come memorizzare nella cache i dati in un documento di Word protetto con una password. Prima che il codice rimuova la protezione nel <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo, Salva il valore corrente in <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> modo che lo stesso tipo di protezione possa essere riapplicato nel <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>Compilare il codice
 Aggiungere questo codice alla `ThisDocument` classe nel progetto. Questo codice presuppone che la password venga archiviata in un campo denominato `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Cache nelle cartelle di lavoro di Excel
 Nei progetti di Excel questa procedura è necessaria solo quando si protegge l'intera cartella di lavoro con una password usando il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodo. Questa procedura non è necessaria se si protegge solo un foglio di foglio specifico con una password usando il <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodo.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Per memorizzare nella cache i dati in una cartella di lavoro di Excel protetta con una password

1. Nella `ThisWorkbook` classe o in una delle classi `Sheet` *n* , contrassegnare un campo o una proprietà pubblica da memorizzare nella cache. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

2. Eseguire l'override del <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo nella `ThisWorkbook` classe e rimuovere la protezione dalla cartella di lavoro.

     Quando la cartella di lavoro viene salvata, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per offrire la possibilità di rimuovere la protezione della cartella di lavoro. Questo consente di salvare le modifiche apportate ai dati memorizzati nella cache.

3. Eseguire l'override del <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo nella `ThisWorkbook` classe e riapplicare la protezione al documento.

     Dopo che la cartella di lavoro è stata salvata, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per offrire la possibilità di riapplicare la protezione alla cartella di lavoro.

### <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come memorizzare nella cache i dati in una cartella di lavoro di Excel protetta con una password. Prima che il codice rimuova la protezione nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo, Salva i <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> valori e correnti <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> , in modo che lo stesso tipo di protezione possa essere riapplicato nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>Compilare il codice
 Aggiungere questo codice alla `ThisWorkbook` classe nel progetto. Questo codice presuppone che la password venga archiviata in un campo denominato `securelyStoredPassword` .

## <a name="see-also"></a>Vedi anche
- [Dati cache](../vsto/caching-data.md)
- [Procedura: memorizzare nella cache i dati per l'uso offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
