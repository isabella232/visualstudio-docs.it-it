---
title: 'Procedura: Dati della cache in un documento protetto da password'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 627469dd3227d82ce1cc97af25d2b8a4537541e5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868446"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>Procedura: Dati della cache in un documento protetto da password
  Se si aggiungono dati alla cache dei dati in un documento o cartella di lavoro è protetto con una password, è possibile che le modifiche ai dati memorizzati nella cache non vengono salvate automaticamente. È possibile salvare le modifiche apportate ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="caching-in-word-documents"></a>La memorizzazione nella cache nei documenti di Word  
  
### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>Per memorizzare i dati in un documento di Word protetto da password  
  
1.  Nel `ThisDocument` classe, contrassegnare un campo pubblico o una proprietà da memorizzare nella cache. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  
  
2.  Eseguire l'override di <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo nel `ThisDocument` classe e rimuovere la protezione dal documento.  
  
     Quando il documento viene salvato, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per dare l'opportunità di rimuovere la protezione del documento. In questo modo le modifiche ai dati memorizzati nella cache deve essere salvato.  
  
3.  Eseguire l'override di <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> metodo nel `ThisDocument` classe e riapplicare la protezione al documento.  
  
     Dopo che il documento viene salvato, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per dare l'opportunità di applicare di nuovo la protezione al documento.  
  
### <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come memorizzare nella cache i dati in un documento di Word protetto da password. Prima che il codice consente di rimuovere la protezione nel <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> metodo, Salva l'oggetto corrente <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> valore, in modo che lo stesso tipo di protezione può essere riapplicato nel <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> (metodo).  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### <a name="compile-the-code"></a>Compilare il codice  
 Aggiungere questo codice per il `ThisDocument` classe nel progetto. Questo codice presuppone che la password viene archiviata in un campo denominato `securelyStoredPassword`.  
  
## <a name="cache-in-excel-workbooks"></a>Memorizzare nella cache nelle cartelle di lavoro di Excel  
 Nei progetti di Excel, questa procedura è necessaria solo quando si protegge l'intera cartella di lavoro con una password utilizzando la <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> (metodo). Questa procedura non è necessaria se si protegge solo un foglio di lavoro specifico con una password utilizzando la <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> (metodo).  
  
### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>Per memorizzare i dati in una cartella di lavoro di Excel protetto da password  
  
1.  Nel `ThisWorkbook` classe o uno dei `Sheet` *n* classi, contrassegnare un campo pubblico o una proprietà da memorizzare nella cache. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  
  
2.  Eseguire l'override di <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo nel `ThisWorkbook` classe e rimuovere la protezione dalla cartella di lavoro.  
  
     Quando la cartella di lavoro viene salvato, la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per dare l'opportunità di rimuovere la protezione della cartella di lavoro. In questo modo le modifiche ai dati memorizzati nella cache deve essere salvato.  
  
3.  Eseguire l'override di <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> metodo nel `ThisWorkbook` classe e riapplicare la protezione al documento.  
  
     Dopo aver salvato la cartella di lavoro, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chiama questo metodo per dare l'opportunità per riapplicare la protezione della cartella di lavoro.  
  
### <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come memorizzare nella cache i dati in una cartella di lavoro di Excel protetto da password. Prima che il codice consente di rimuovere la protezione nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> metodo, Salva l'oggetto corrente <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> e <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> i valori, in modo che lo stesso tipo di protezione può essere riapplicato nel <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> (metodo).  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### <a name="compile-the-code"></a>Compilare il codice  
 Aggiungere questo codice per il `ThisWorkbook` classe nel progetto. Questo codice presuppone che la password viene archiviata in un campo denominato `securelyStoredPassword`.  
  
## <a name="see-also"></a>Vedere anche  
 [Dati della cache](../vsto/caching-data.md)   
 [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: Memorizzare nella cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
