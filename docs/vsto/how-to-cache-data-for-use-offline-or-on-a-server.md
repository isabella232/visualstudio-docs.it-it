---
title: "Procedura: Memorizzare nella cache i dati per l'uso offline o in un server"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 671b4c18963be4f9c81e15fe33e5d68a410655c9
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804656"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procedura: Memorizzare nella cache i dati per l'uso offline o in un server
  È possibile contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. Questo inoltre rende possibile per i dati del documento deve essere modificato da un altro codice quando il documento viene archiviato in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile contrassegnare un elemento di dati da memorizzare nella cache quando l'elemento di dati viene dichiarato nel codice, o, se si usa un' <xref:System.Data.DataSet>, impostando una proprietà **proprietà** finestra. Se si è la memorizzazione nella cache un elemento di dati che non è un <xref:System.Data.DataSet> o <xref:System.Data.DataTable>, assicurarsi che vengano soddisfatti i criteri per la memorizzazione nella cache del documento. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).

> [!NOTE]
>  I set di dati creati utilizzando Visual Basic che sono contrassegnati come **memorizzata nella cache** e **WithEvents** (inclusi i set di dati vengono trascinati dal **Zdroje dat** finestra o **Casella degli strumenti** che hanno il **CacheInDocument** impostata su **True**) hanno un carattere di sottolineatura come prefisso per i relativi nomi nella cache. Ad esempio, se si crea un set di dati e denominarlo **clienti**, il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nome sarà **Customers** nella cache. Quando si usa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere a questo elemento memorizzato nella cache, è necessario specificare **Customers** anziché **clienti**.

### <a name="to-cache-data-in-the-document-using-code"></a>Per memorizzare i dati nel documento usando il codice

1.  Dichiarare un campo pubblico o una proprietà per l'elemento di dati come membro di una classe di elementi host nel progetto, ad esempio la `ThisDocumen`classe t in un progetto di Word o `ThisWorkbook` classe in un progetto di Excel.

2.  Applicare il <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo per il membro per contrassegnare l'elemento di dati da archiviare nella cache di dati del documento. Nell'esempio seguente si applica questo attributo a una dichiarazione di campo per un <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  Aggiungere il codice per creare un'istanza dell'elemento di dati e, se applicabile, caricarlo dal database.

     L'elemento di dati viene caricato solo quando viene creato inizialmente; Successivamente, la cache rimane associata al documento ed è necessario scrivere altro codice per eseguire l'aggiornamento.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Per memorizzare nella cache un set di dati del documento utilizzando la finestra proprietà

1.  Aggiungere il set di dati al progetto usando gli strumenti di progettazione di Visual Studio, ad esempio, aggiungendo un'origine dati al progetto utilizzando il **Zdroje dat** finestra.

2.  Creare un'istanza del set di dati se non si è già presente e selezionare l'istanza nella finestra di progettazione.

3.  Nel **le proprietà** impostare nella finestra di **CacheInDocument** proprietà **True**.

     Per altre informazioni, vedere [delle proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).

4.  Nel **proprietà** impostare nella finestra di **modificatori** proprietà **pubblica** (per impostazione predefinita è **interno**).

## <a name="see-also"></a>Vedere anche
 [I dati nella cache](../vsto/caching-data.md) [come: Memorizzare nella cache a livello di codice di un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) [come: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md) [accedere ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md) [salvare i dati](../data-tools/saving-data.md)
