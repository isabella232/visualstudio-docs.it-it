---
title: Salvataggio permanente dei dati nel MSBuild Project file | Microsoft Docs
description: Informazioni su come rendere persistenti i dati in un file di progetto e usare IPersistXMLFragment per mantenere i dati nel file di progetto nei livelli di aggregazione dei sottotipi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a5147eed5026f010811905fa693baccb4352010e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063083"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Salvataggio permanente dei dati nel file di progetto MSBuild
Un sottotipo di progetto potrebbe dover rendere persistenti i dati specifici del sottotipo nel file di progetto per un uso successivo. Un sottotipo di progetto usa la persistenza del file di progetto per soddisfare i requisiti seguenti:

1. Rendere persistenti i dati usati durante la compilazione del progetto. Per altre informazioni sul Microsoft Build Engine, vedere [MSBuild](../../msbuild/msbuild.md). Le informazioni relative alla compilazione possono:

    1. Dati indipendenti dalla configurazione. In altri termini, i dati archiviati MSBuild elementi con condizioni vuote o mancanti.

    2. Dati dipendenti dalla configurazione. In altri casi, i dati archiviati MSBuild elementi condizionati per una particolare configurazione di progetto. Esempio:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Rendere persistenti i dati non rilevanti per la compilazione. Questi dati possono essere espressi in xml in formato libero che non viene convalidato rispetto a un XML Schema.

    1. Dati indipendenti dalla configurazione.

    2. Dati dipendenti dalla configurazione.

## <a name="persisting-build-related-information"></a>Persistenza delle Build-Related dati
 La persistenza dei dati utili per la compilazione di un progetto viene gestita tramite MSBuild. Il MSBuild gestisce una tabella master di informazioni correlate alla compilazione. Project sottotipi sono responsabili dell'accesso a questi dati per ottenere e impostare i valori delle proprietà. Project sottotipi possono anche aumentare la tabella dati correlata alla compilazione aggiungendo altre proprietà da rendere persistenti e rimuovendo le proprietà in modo che non siano persistenti.

 Per modificare i MSBuild, un sottotipo di progetto è responsabile del recupero dell'oggetto MSBuild proprietà dal sistema del progetto di base tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> è un'interfaccia implementata nel sistema di progetto di base e le query di sottotipo di progetto di aggregazione per il progetto eseguendo `QueryInterface` .

 Nella procedura seguente vengono descritti i passaggi per la rimozione di una proprietà tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Per rimuovere una proprietà da un file MSBuild progetto

1. Chiamare `QueryInterface` su <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del sottotipo di progetto.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con impostato sulla proprietà che si vuole `pszPropName` rimuovere.

### <a name="persisting-non-build-related-information"></a>Persistenza delle informazioni correlate alla non compilazione
 La persistenza dei dati nei file di progetto che non è importante compilare viene gestita tramite <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .

 È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implementare sull'oggetto `project subtype aggregator` principale, `project subtype project configuration` sull'oggetto o su entrambi.

 I punti seguenti illustrano i concetti principali relativi alla persistenza di informazioni non correlate alla compilazione.

- Il progetto di base chiama sull'oggetto aggregatore del sottotipo di progetto principale (ovvero il sottotipo di progetto più esterno) per caricare e salvare i dati indipendenti dalla configurazione e chiama sugli oggetti di configurazione del progetto del sottotipo di progetto per caricare o salvare i dati dipendenti dalla configurazione.

- Il progetto di base chiama più volte i metodi di per ogni livello di aggregazione del sottotipo di progetto e passa il <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> GUID per ogni livello.

- Il progetto di base passa o riceve un frammento XML dedicato a un sottotipo di progetto specifico e usa questo meccanismo per rendere persistente lo stato tra i livelli di aggregazione.

- Il progetto di base chiama l'implementazione del sottotipo di progetto più <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> esterno passando un GUID. Se il GUID appartiene al sottotipo di progetto più esterno, gestisce la chiamata stessa; In caso contrario delega la chiamata a un sottotipo di progetto interno e così via, fino a quando non viene trovato il sottotipo di progetto a cui corrisponde il GUID.

- Un sottotipo di progetto può anche modificare il frammento XML prima o dopo la delega della chiamata a un sottotipo di progetto interno. Nell'esempio seguente viene illustrato un estratto di un file di progetto, in cui un nome di un file che contiene proprietà specifiche di un sottotipo di progetto viene passato a tale sottotipo di progetto.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Vedi anche
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)
