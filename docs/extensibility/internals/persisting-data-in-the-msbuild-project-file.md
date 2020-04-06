---
title: Rendere persistenti i dati nel file di progetto MSBuild Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706688"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Salvataggio permanente dei dati nel file di progetto MSBuild
Un sottotipo di progetto potrebbe essere necessario rendere persistenti i dati specifici del sottotipo nel file di progetto per un utilizzo successivo. Un sottotipo di progetto utilizza la persistenza del file di progetto per soddisfare i requisiti seguenti:A project subtype uses project file persistence to meet the following requirements:

1. Rendere persistenti i dati utilizzati durante la compilazione del progetto. (Per ulteriori informazioni sul motore Microsoft Build, vedere [MSBuild](../../msbuild/msbuild.md). Le informazioni relative alla compilazione possono:Build-related information can either:

    1. Dati indipendenti dalla configurazione. Ovvero, i dati archiviati in elementi MSBuild con condizioni vuote o mancanti.

    2. Dati dipendenti dalla configurazione. Ovvero, i dati archiviati in elementi MSBuild che sono condizionati per una particolare configurazione di progetto. Ad esempio:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Rendere persistenti i dati non rilevanti per la compilazione. Questi dati possono essere espressi in formato XML in formato libero che non viene convalidato rispetto a uno schema XML.

    1. Dati indipendenti dalla configurazione.

    2. Dati dipendenti dalla configurazione.

## <a name="persisting-build-related-information"></a>Persistenza delle informazioni relative alla compilazionePersisting Build-Related Information
 La persistenza dei dati utili per la compilazione di un progetto viene gestita tramite MSBuild.Persistence of data useful for building a project is handled through MSBuild. Il sistema MSBuild gestisce una tabella master di informazioni relative alla compilazione. I sottotipi di progetto sono responsabili dell'accesso a questi dati per ottenere e impostare i valori delle proprietà. I sottotipi di progetto possono anche aumentare la tabella di dati correlati alla compilazione aggiungendo proprietà aggiuntive da rendere persistenti e rimuovendo le proprietà in modo che non vengano rese persistenti.

 Per modificare i dati MSBuild, un sottotipo di progetto è responsabile del <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>recupero dell'oggetto proprietà MSBuild dal sistema del progetto di base tramite . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>è un'interfaccia implementata nel sistema di progetto principale e `QueryInterface`l'aggregazione di query di sottotipo di progetto eseguendo .

 Nella procedura seguente vengono descritti i passaggi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>per la rimozione di una proprietà mediante .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Per rimuovere una proprietà da un file di progetto MSBuildTo remove a property from an MSBuild project file

1. Chiamare `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> il sottotipo di progetto.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` con impostato sulla proprietà che si desidera rimuovere.

### <a name="persisting-non-build-related-information"></a>Persistenza di informazioni non correlate alla compilazionePersisting Non-Build Related Information
 La persistenza dei dati nei file di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>che non è importante compilare viene gestita tramite .

 È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementare `project subtype aggregator` l'oggetto principale, l'oggetto `project subtype project configuration` o entrambi.

 I punti seguenti illustrano i concetti principali relativi alla persistenza di informazioni non correlate alla compilazione.

- Il progetto di base chiama l'oggetto aggregatore del sottotipo di progetto principale (ovvero il sottotipo di progetto più esterno) per caricare e salvare dati indipendenti dalla configurazione e chiama gli oggetti di configurazione del progetto di sottotipo di progetto per caricare o salvare i dati dipendenti dalla configurazione.

- Il progetto di base <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> chiama i metodi di più volte per ogni livello di aggregazione del sottotipo di progetto e passa il GUID per ogni livello.

- Il progetto di base passa o riceve un frammento XML dedicato a un particolare sottotipo di progetto e utilizza questo meccanismo per mantenere lo stato tra i livelli di aggregazione.

- Il progetto di base chiama l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>sottotipo di progetto più esterno passando un GUID. Se il GUID appartiene al sottotipo di progetto più esterno, gestisce la chiamata stessa; in caso contrario, delega la chiamata a un sottotipo di progetto interno e così via, fino a quando non viene trovato il sottotipo di progetto a cui corrisponde il GUID.

- Un sottotipo di progetto può anche modificare il frammento XML prima o dopo la delega della chiamata a un sottotipo di progetto interno. Nell'esempio seguente viene illustrato un estratto da un file di progetto, in cui un nome di un file che contiene proprietà specifiche di un sottotipo di progetto, viene passato a tale sottotipo di progetto.

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
