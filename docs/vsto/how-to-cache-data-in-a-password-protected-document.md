---
title: 'Procedura: Memorizzare nella cache i dati in un documento protetto da password'
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ccdb906022d4dcfc321af294eec59afa36832773
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824185"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procedura: Memorizzare nella cache i dati in un documento protetto da password
  Se si aggiungono dati alla cache dei dati in un documento o in una cartella di lavoro protetta con una password, le modifiche ai dati memorizzati nella cache non vengono salvate automaticamente. È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Memorizzazione nella cache nei documenti di Word

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Per memorizzare nella cache i dati in un documento di Word protetto con una password

1. Nella classe contrassegnare un campo o una `ThisDocument` proprietà pubblica da memorizzare nella cache. Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).

2. Eseguire <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> l'override del metodo `ThisDocument` nella classe e rimuovere la protezione dal documento.

     Quando il documento viene salvato, chiama questo metodo per offrire la possibilità di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuovere la protezione del documento. In questo modo è possibile salvare le modifiche ai dati memorizzati nella cache.

3. Eseguire <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> l'override del metodo `ThisDocument` nella classe e riapplicare la protezione al documento.

     Dopo aver salvato il documento, chiama questo metodo per offrire la possibilità di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] riapplicare la protezione al documento.

### <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come memorizzare nella cache i dati in un documento di Word protetto con una password. Prima che il codice rimova la protezione nel metodo , salva il valore corrente, in modo che lo stesso tipo di protezione possa essere <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> riapplicato nel <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb" id="Snippet1":::

### <a name="compile-the-code"></a>Compilare il codice
 Aggiungere questo codice alla `ThisDocument` classe nel progetto. Questo codice presuppone che la password sia archiviata in un campo denominato `securelyStoredPassword` .

## <a name="cache-in-excel-workbooks"></a>Memorizzare nella cache le cartelle di lavoro di Excel
 Nei progetti Excel questa procedura è necessaria solo quando si protegge l'intera cartella di lavoro con una password usando il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodo . Questa procedura non è necessaria se si protegge solo un foglio di lavoro specifico con una password usando il <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metodo .

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Per memorizzare nella cache i dati in una cartella di lavoro di Excel protetta con una password

1. Nella classe `ThisWorkbook` o in una delle classi n contrassegnare un campo o una proprietà pubblica da `Sheet`  memorizzare nella cache. Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).

2. Eseguire <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> l'override del metodo `ThisWorkbook` nella classe e rimuovere la protezione dalla cartella di lavoro.

     Quando la cartella di lavoro viene salvata, chiama questo metodo per offrire la possibilità di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuovere la protezione della cartella di lavoro. In questo modo è possibile salvare le modifiche ai dati memorizzati nella cache.

3. Eseguire <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> l'override del metodo `ThisWorkbook` nella classe e riapplicare la protezione al documento.

     Dopo aver salvato la cartella di lavoro, chiama questo metodo per offrire la possibilità di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] riapplicare la protezione alla cartella di lavoro.

### <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come memorizzare nella cache i dati in una cartella di lavoro di Excel protetta con una password. Prima che il codice rimova la protezione nel metodo , salva i valori e correnti, in modo che lo stesso tipo di protezione possa essere <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> riapplicato nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs" id="Snippet1":::

### <a name="compile-the-code"></a>Compilare il codice
 Aggiungere questo codice alla `ThisWorkbook` classe nel progetto. Questo codice presuppone che la password sia archiviata in un campo denominato `securelyStoredPassword` .

## <a name="see-also"></a>Vedi anche
- [Dati cache](../vsto/caching-data.md)
- [Procedura: Memorizzare nella cache i dati da usare offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: Memorizzare nella cache un'origine dati in un documento di Office a livello di codice](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
