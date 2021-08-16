---
title: Memorizzare nella cache l'origine dati Office documento a livello di codice
description: Informazioni su come aggiungere a livello di codice un oggetto dati alla cache dei dati in un documento chiamando il metodo StartCaching di un elemento host.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: eeede798542499d6a482b1a42b626e73170d024e864ec941c66e72a1b131bba3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408773"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Procedura: Memorizzare nella cache un'origine dati in un documento Office codice
  È possibile aggiungere a livello di codice un oggetto dati alla cache dei dati in un documento chiamando il metodo di un elemento host, ad esempio `StartCaching` <xref:Microsoft.Office.Tools.Word.Document> , o <xref:Microsoft.Office.Tools.Excel.Workbook> <xref:Microsoft.Office.Tools.Excel.Worksheet> . Rimuovere un oggetto dati dalla cache dei dati chiamando il `StopCaching` metodo di un elemento host.

 Il `StartCaching` metodo e il metodo sono entrambi `StopCaching` privati, ma vengono visualizzati in IntelliSense.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Quando si usa il metodo per aggiungere un oggetto dati alla cache dei dati, non è necessario dichiarare l'oggetto dati `StartCaching` con <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> l'attributo . Tuttavia, l'oggetto dati deve soddisfare determinati requisiti per essere aggiunto alla cache dei dati. Per altre informazioni, vedere [Memorizzare i dati nella cache.](../vsto/caching-data.md)

## <a name="to-programmatically-cache-a-data-object"></a>Per memorizzare nella cache un oggetto dati a livello di codice

1. Dichiarare l'oggetto dati a livello di classe, non all'interno di un metodo. In questo esempio si presuppone che si dichiara un oggetto denominato <xref:System.Data.DataSet> che `dataSet1` si desidera memorizzare nella cache a livello di codice.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet12":::

2. Creare un'istanza dell'oggetto dati, quindi chiamare il metodo dell'istanza del documento o del foglio di lavoro e passare `StartCaching` il nome dell'oggetto dati.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet13":::

## <a name="to-stop-caching-a-data-object"></a>Per interrompere la memorizzazione nella cache di un oggetto dati

1. Chiamare il `StopCaching` metodo dell'istanza del documento o del foglio di lavoro e passare il nome dell'oggetto dati. In questo esempio si presuppone che sia presente un <xref:System.Data.DataSet> oggetto denominato che si desidera interrompere la `dataSet1` memorizzazione nella cache.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet14":::

    > [!NOTE]
    > Non chiamare dal `StopCaching` gestore eventi per l'evento `Shutdown` di un documento o di un foglio di lavoro. Quando viene generato `Shutdown` l'evento, è troppo tardi per modificare la cache dei dati. Per altre informazioni `Shutdown` sull'evento, vedere [Eventi in Office progetti](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Vedi anche

- [Dati cache](../vsto/caching-data.md)
- [Procedura: Memorizzare nella cache i dati per l'uso offline o in un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Procedura: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Salvare i dati](../data-tools/save-data-back-to-the-database.md)
