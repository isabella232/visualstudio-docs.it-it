---
title: Rendere persistenti i dati nel File di progetto MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 307e8e5285dd0023d30772c5eac7a4e351287aa5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060931"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Salvataggio permanente dei dati nel file di progetto MSBuild
Un sottotipo di progetto potrebbe essere necessario rendere persistenti i dati specifici del sottotipo nel file di progetto per un uso successivo. Un sottotipo di progetto usa la persistenza del file di progetto per soddisfare i requisiti seguenti:

1. Rendere persistenti i dati usati come parte della compilazione del progetto. (Per altre informazioni su Microsoft Build Engine, vedere [MSBuild](../../msbuild/msbuild.md).) Le informazioni relative alla compilazione possono:

    1. Dati indipendenti dalla configurazione. Vale a dire i dati archiviati negli elementi di MSBuild con condizioni vuoti o mancanti.

    2. Dati dipendenti dalla configurazione. Vale a dire i dati archiviati in elementi di MSBuild che sono condizionati per una configurazione particolare progetto. Ad esempio:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Rendere persistenti i dati che non sono rilevanti per compilare. Questi dati possono essere espresse in formato XML in formato libero che non viene convalidato rispetto a uno schema XML.

    1. Dati indipendenti dalla configurazione.

    2. Dati dipendenti dalla configurazione.

## <a name="persisting-build-related-information"></a>Persistenza delle informazioni relative alla compilazione
 Persistenza dei dati utile per la creazione di un progetto viene gestita tramite MSBuild. Il sistema MSBuild gestisce una tabella master di informazioni relative alla compilazione. Sottotipi di progetto sono responsabili per l'accesso a questi dati per ottenere e impostare i valori delle proprietà. Sottotipi di progetto possono anche aumentare la tabella di dati correlati alla compilazione aggiungendo proprietà aggiuntive da rendere persistenti e rimuovendo le proprietà in modo che non vengano mantenuti.

 Per modificare i dati di MSBuild, un sottotipo di progetto è responsabile per il recupero dell'oggetto di proprietà MSBuild dal sistema di progetto di base tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> è un'interfaccia implementata nel sistema di progetto di base e le query di sottotipo di progetto aggregazione per tale eseguendo `QueryInterface`.

 La procedura seguente illustra i passaggi per la rimozione di una proprietà usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Per rimuovere una proprietà da un file di progetto MSBuild

1. Chiamare `QueryInterface` su <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> del sottotipo di progetto.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> con `pszPropName` impostato sulla proprietà che si desidera rimuovere.

### <a name="persisting-non-build-related-information"></a>Rendere persistenti le informazioni correlate a Non-Build
 Persistenza dei dati nei file di progetto che non è rilevante per compilare è gestita tramite <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 È possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> nella classe principale `project subtype aggregator` oggetto, il `project subtype project configuration` oggetto, o entrambi.

 Quanto riportato di seguito illustrano i concetti principali relativi la persistenza delle informazioni correlate di non compilazione.

- Chiama al progetto di base sull'oggetto progetto principale sottotipo (vale a dire, il sottotipo di progetto più esterno) Sil aggregator per caricare e salvare i dati di configurazione indipendente e chiama gli oggetti di configurazione progetto progetto sottotipo per caricare o salvare la configurazione dipendente dati.

- Il progetto di base chiama i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> più volte per ogni livello di aggregazione sottotipo di progetto e passa il GUID per ogni livello.

- Il progetto di base passa o riceve un frammento XML che è dedicato a un sottotipo di progetto specifico e Usa questo meccanismo come un modo per salvare in modo permanente lo stato tra i livelli di aggregazione.

- Il progetto di base chiama il sottotipo di progetto più esterno <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementazione passando un GUID. Se il GUID a cui appartiene il sottotipo di progetto più esterno, gestisce la chiamata. in caso contrario, delega la chiamata a un sottotipo del progetto interno e così via, fino a quando non viene trovato il sottotipo del progetto corrispondente al GUID.

- Un sottotipo di progetto è possibile modificare anche il frammento XML prima o dopo che delega la chiamata a un sottotipo del progetto interno. Nell'esempio seguente viene illustrato un estratto da un file di progetto, in cui viene passato un nome di un file che contiene le proprietà specifiche di un sottotipo di progetto, per il sottotipo di progetto.

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