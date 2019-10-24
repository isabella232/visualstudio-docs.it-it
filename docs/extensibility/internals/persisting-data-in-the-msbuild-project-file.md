---
title: Salvataggio permanente dei dati nel file di progetto MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7772f633c44c50b24995b7cc8a3f2f8bbbb01863
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726057"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Salvataggio permanente dei dati nel file di progetto MSBuild
Un sottotipo di progetto potrebbe avere la necessità di salvare in modo permanente i dati specifici del sottotipo nel file di progetto per un uso successivo. Un sottotipo di progetto usa la persistenza dei file di progetto per soddisfare i requisiti seguenti:

1. Rende permanente i dati utilizzati come parte della compilazione del progetto. Per ulteriori informazioni sulla Microsoft Build Engine, vedere [MSBuild](../../msbuild/msbuild.md). Le informazioni correlate alla compilazione possono essere:

    1. Dati indipendenti dalla configurazione. Ovvero i dati archiviati negli elementi MSBuild con condizioni vuote o mancanti.

    2. Dati dipendenti dalla configurazione. Ovvero i dati archiviati negli elementi MSBuild che sono condizionati per una particolare configurazione del progetto. Esempio:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Rende permanente i dati non rilevanti per la compilazione. Questi dati possono essere espressi in formato XML libero che non viene convalidato rispetto a un XML Schema.

    1. Dati indipendenti dalla configurazione.

    2. Dati dipendenti dalla configurazione.

## <a name="persisting-build-related-information"></a>Salvataggio permanente delle informazioni correlate alla compilazione
 La persistenza dei dati utile per la compilazione di un progetto viene gestita tramite MSBuild. Il sistema MSBuild gestisce una tabella master di informazioni correlate alla compilazione. I sottotipi di progetto sono responsabili dell'accesso a questi dati per ottenere e impostare i valori delle proprietà. I sottotipi di progetto possono anche aumentare la tabella dei dati correlati alla compilazione aggiungendo proprietà aggiuntive da rendere permanente e rimuovendo le proprietà in modo che non siano rese permanente.

 Per modificare i dati MSBuild, un sottotipo di progetto è responsabile del recupero dell'oggetto proprietà MSBuild dal sistema del progetto di base tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> è un'interfaccia implementata nel sistema di progetto di base e il sottotipo di aggregazione del progetto esegue query su di esso eseguendo `QueryInterface`.

 Nella procedura riportata di seguito vengono illustrati i passaggi per la rimozione di una proprietà utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Per rimuovere una proprietà da un file di progetto MSBuild

1. Chiamare `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del sottotipo di progetto.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` impostato sulla proprietà che si desidera rimuovere.

### <a name="persisting-non-build-related-information"></a>Salvataggio permanente di informazioni non correlate alla compilazione
 La persistenza dei dati nei file di progetto che non è rilevante per la compilazione viene gestita tramite <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 È possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sull'oggetto `project subtype aggregator` principale, sull'oggetto `project subtype project configuration` o su entrambi.

 Nei punti seguenti vengono illustrati i principali concetti relativi alla persistenza delle informazioni non correlate alla compilazione.

- Il progetto di base chiama il sottotipo di progetto principale, ovvero l'oggetto Aggregator del sottotipo di progetto più esterno, per caricare e salvare i dati indipendenti dalla configurazione e chiama sugli oggetti di configurazione del progetto sottotipo di progetto per caricare o salvare la configurazione dipendente dati.

- Il progetto di base chiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> più volte per ogni livello di aggregazione del sottotipo di progetto e passa il GUID per ogni livello.

- Il progetto di base passa o riceve un frammento XML dedicato a un sottotipo di progetto specifico e utilizza questo meccanismo come metodo per la permanenza dello stato tra i livelli di aggregazione.

- Il progetto di base chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementation del sottotipo di progetto più esterno passando un GUID. Se il GUID appartiene al sottotipo di progetto più esterno, gestisce la chiamata stessa; in caso contrario, delega la chiamata a un sottotipo di progetto interno e così via fino a quando non viene trovato il sottotipo di progetto a cui corrisponde il GUID.

- Un sottotipo di progetto può anche modificare il frammento XML prima o dopo la delega della chiamata a un sottotipo di progetto interno. Nell'esempio seguente viene illustrato un Estratto da un file di progetto, in cui il nome di un file che contiene le proprietà specifiche di un sottotipo di progetto viene passato a tale sottotipo di progetto.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Vedere anche
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)