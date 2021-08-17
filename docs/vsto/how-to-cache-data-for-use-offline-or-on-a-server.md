---
title: 'Procedura: Memorizzare nella cache i dati da usare offline o in un server'
description: Contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. In questo modo è possibile che i dati nel documento siano manipolati da altro codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2cdb6958214e7d7636a722541f82bca7469c9e246ae4b8218b734b86646a43fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351928"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procedura: Memorizzare nella cache i dati da usare offline o in un server
  È possibile contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. In questo modo è anche possibile che i dati nel documento siano manipolati da altro codice quando il documento viene archiviato in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile contrassegnare un elemento dati da memorizzare nella cache quando l'elemento di dati viene dichiarato nel codice o, se si usa , impostando una proprietà nella <xref:System.Data.DataSet> **finestra** Proprietà. Se si memorizza nella cache un elemento di dati che non è o , assicurarsi che soddisfi i criteri per la <xref:System.Data.DataSet> <xref:System.Data.DataTable> memorizzazione nella cache del documento. Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).

> [!NOTE]
> I set di dati creati usando Visual Basic contrassegnati come **Memorizzati** nella cache e  **WithEvents**  (inclusi i set di dati trascinati dalla finestra Origini dati o dalla casella degli strumenti con la proprietà **CacheInDocument** impostata su **True)** hanno un carattere di sottolineatura preceduto dai relativi nomi nella cache. Ad esempio, se si crea un set di dati e lo si chiama **Customers**, il nome verrà _Customers <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nella cache.  Quando si usa per accedere a questo elemento memorizzato nella cache, è necessario specificare <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> **_Customers** anziché **Customers**.

### <a name="to-cache-data-in-the-document-using-code"></a>Per memorizzare nella cache i dati nel documento usando il codice

1. Dichiarare un campo pubblico o una proprietà per l'elemento di dati come membro di una classe di elemento host nel progetto, ad esempio la classe t in un progetto Word o la classe in un `ThisDocumen` `ThisWorkbook` progetto Excel progetto.

2. Applicare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> l'attributo al membro per contrassegnare l'elemento di dati da archiviare nella cache dei dati del documento. Nell'esempio seguente questo attributo viene applicato a una dichiarazione di campo per <xref:System.Data.DataSet> un oggetto .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet11":::

3. Aggiungere il codice per creare un'istanza dell'elemento dati e, se applicabile, caricarlo dal database.

     L'elemento dati viene caricato solo quando viene creato per la prima volta. successivamente, la cache rimane con il documento ed è necessario scrivere altro codice per aggiornarlo.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Per memorizzare nella cache un set di dati nel documento usando il Finestra Proprietà

1. Aggiungere il set di dati al progetto usando gli strumenti di progettazione Visual Studio, ad esempio aggiungendo un'origine dati al progetto usando la **finestra Origini** dati .

2. Creare un'istanza del set di dati, se non ne è già presente una, e selezionare l'istanza nella finestra di progettazione.

3. Nella finestra **Proprietà** impostare la **proprietà CacheInDocument** su **True.**

     Per altre informazioni, vedere [Proprietà in Office Projects](../vsto/properties-in-office-projects.md).

4. Nella finestra **Proprietà** impostare la **proprietà Modifiers** su **Public** (per impostazione predefinita **è Internal).**

## <a name="see-also"></a>Vedi anche
- [Dati cache](../vsto/caching-data.md)
- [Procedura: Memorizzare nella cache un'origine dati in un documento Office codice](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Procedura: Memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accedere ai dati nei documenti nel server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Salvare i dati](../data-tools/save-data-back-to-the-database.md)
