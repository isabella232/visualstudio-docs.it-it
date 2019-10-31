---
title: Origine dati della cache nel documento di Office a livello di codice
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241ce42c2d411fdaf611f3a7f2b52eb40c8c32a2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189588"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office
  È possibile aggiungere a livello di codice un oggetto dati alla cache dei dati in un documento chiamando il metodo `StartCaching` di un elemento host, ad esempio <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>o <xref:Microsoft.Office.Tools.Excel.Worksheet>. Rimuovere un oggetto dati dalla cache dei dati chiamando il metodo `StopCaching` di un elemento host.

 Il metodo `StartCaching` e il metodo `StopCaching` sono entrambi privati, ma vengono visualizzati in IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Quando si utilizza il metodo `StartCaching` per aggiungere un oggetto dati alla cache di dati, non è necessario dichiarare l'oggetto dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Tuttavia, l'oggetto dati deve soddisfare determinati requisiti da aggiungere alla cache di dati. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Per memorizzare nella cache a livello di codice un oggetto dati

1. Dichiarare l'oggetto dati a livello di classe, non all'interno di un metodo. Questo esempio presuppone che si stia dichiarando un <xref:System.Data.DataSet> denominato `dataSet1` che si vuole memorizzare nella cache a livello di codice.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Creare un'istanza dell'oggetto dati, quindi chiamare il metodo `StartCaching` dell'istanza Document o Worksheet e passare il nome dell'oggetto dati.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>Per arrestare la memorizzazione nella cache di un oggetto dati

1. Chiamare il metodo `StopCaching` dell'istanza Document o Worksheet e passare il nome dell'oggetto dati. In questo esempio si presuppone che si disponga di un <xref:System.Data.DataSet> denominato `dataSet1` che si desidera arrestare la memorizzazione nella cache.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Non chiamare `StopCaching` dal gestore eventi per l'evento `Shutdown` di un documento o di un foglio di esecuzione. Quando viene generato l'evento `Shutdown`, è troppo tardi per modificare la cache dei dati. Per ulteriori informazioni sull'evento `Shutdown`, vedere [eventi nei progetti di Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Vedere anche

- [Dati della cache](../vsto/caching-data.md)
- [Procedura: memorizzare nella cache i dati per l'uso offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Salva dati](../data-tools/save-data-back-to-the-database.md)
