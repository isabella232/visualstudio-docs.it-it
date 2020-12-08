---
title: "Procedura: memorizzare nella cache i dati per l'uso offline o su un server"
description: Contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. In questo modo è possibile che i dati del documento vengano modificati da altro codice.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cefd4cd132e75f8ff622c8e0d809d317242c10f5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844322"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Procedura: memorizzare nella cache i dati per l'uso offline o su un server
  È possibile contrassegnare un elemento di dati da memorizzare nella cache del documento, in modo che sia disponibile offline. Ciò consente anche di modificare i dati nel documento da altro codice quando il documento viene archiviato in un server.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È possibile contrassegnare un elemento di dati da memorizzare nella cache quando l'elemento dati viene dichiarato nel codice o, se si utilizza un <xref:System.Data.DataSet> , impostando una proprietà nella finestra **Proprietà** . Se si memorizza nella cache un elemento di dati che non è <xref:System.Data.DataSet> o <xref:System.Data.DataTable> , verificare che soddisfi i criteri per la memorizzazione nella cache del documento. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

> [!NOTE]
> I set di dati creati utilizzando Visual Basic contrassegnati come **memorizzati nella cache** e **WithEvents** (inclusi i set di dati trascinati dalla finestra **origini dati** o dalla **casella degli strumenti** la cui proprietà **CacheInDocument** è impostata su **true**) hanno un carattere di sottolineatura preceduto dai rispettivi nomi nella cache. Se, ad esempio, si crea un set di dati e lo si assegna al nome **Customers**, il <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nome verrà **_Customers** nella cache. Quando si utilizza <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere a questo elemento memorizzato nella cache, è necessario specificare **_Customers** anziché **i clienti**.

### <a name="to-cache-data-in-the-document-using-code"></a>Per memorizzare nella cache i dati nel documento usando il codice

1. Dichiarare una proprietà o un campo pubblico per l'elemento di dati come membro di una classe di elementi host nel progetto, ad esempio la `ThisDocumen` classe t in un progetto di Word o la `ThisWorkbook` classe in un progetto di Excel.

2. Applicare l' <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attributo al membro per contrassegnare l'elemento di dati da archiviare nella cache dei dati del documento. Nell'esempio seguente l'attributo viene applicato a una dichiarazione di campo per un oggetto <xref:System.Data.DataSet> .

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Aggiungere codice per creare un'istanza dell'elemento di dati e, se applicabile, per caricarlo dal database.

     L'elemento di dati viene caricato solo quando viene creato per la prima volta. Successivamente, la cache rimane associata al documento ed è necessario scrivere altro codice per aggiornarlo.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Per memorizzare nella cache un set di dati nel documento utilizzando il Finestra Proprietà

1. Aggiungere il set di dati al progetto utilizzando gli strumenti della finestra di progettazione di Visual Studio, ad esempio aggiungendo un'origine dati al progetto utilizzando la finestra **origini dati** .

2. Creare un'istanza del set di dati, se non ne è già presente uno, e selezionare l'istanza nella finestra di progettazione.

3. Nella finestra **Proprietà** impostare la proprietà **CacheInDocument** su **true**.

     Per altre informazioni, vedere [proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).

4. Nella finestra **Proprietà** impostare la proprietà **Modifiers** su **public** (per impostazione predefinita è **Internal**).

## <a name="see-also"></a>Vedi anche
- [Dati cache](../vsto/caching-data.md)
- [Procedura: memorizzare nella cache a livello di codice un'origine dati in un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Procedura: memorizzare nella cache i dati in un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Accedere ai dati nei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Salvare i dati](../data-tools/save-data-back-to-the-database.md)
