---
title: Cenni preliminari sulle opzioni di configurazione - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709415"
---
# <a name="configuration-options-overview"></a>Panoramica delle opzioni di configurazione
I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti in possono supportare più configurazioni che possono essere compilate, sottoposte a debug, eseguite e/o distribuite. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà, in genere opzioni del compilatore e percorsi di file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni, *Debug* e *Release*. Queste configurazioni possono essere applicate utilizzando le impostazioni predefinite o modificate per soddisfare i requisiti specifici della soluzione e/o del progetto. Alcuni pacchetti possono essere compilati in due modi: come editor ActiveX o come componente sul posto. Tuttavia, i progetti non devono supportare configurazioni multiple. Se è disponibile una sola configurazione, tale configurazione viene mappata in tutte le configurazioni della soluzione.

 Le configurazioni sono in genere costituite da due parti: il nome della configurazione (ad esempio *Debug* o *Release*) e le impostazioni della piattaforma. Il nome di piattaforma di una configurazione identifica l'ambiente di destinazione della configurazione, ad esempio un set di API o una piattaforma del sistema operativo. Gli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utenti di non possono creare una piattaforma; devono scegliere tra le selezioni che un progetto VSPackage consente. Quando un utente installa un pacchetto VSPackage, la piattaforma di recapito creata durante lo sviluppo del pacchetto può esporre qualsiasi nome di piattaforma desiderato in base a qualsiasi criterio impostato dal creatore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme rese disponibili tramite il pacchetto VSPackage quando viene creata un'istanza delle pagine delle proprietà.

 I nomi delle piattaforme sono facoltativi poiché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non dispone di un nome di piattaforma, la stringa **N/D** viene visualizzata nell'interfaccia utente.

 Ogni soluzione ha un proprio set di configurazioni, solo una delle quali può essere attiva alla volta. Una configurazione di soluzione è un set di non più di una configurazione da ogni progetto. La clausola "non più di" è dovuta all'opzione per escludere un progetto da una configurazione di soluzione. Gli utenti possono creare configurazioni di soluzione personalizzate.

 Nella tabella seguente viene illustrata l'impostazione tipica delle configurazioni per un progetto. Le righe sono etichettate con i nomi di configurazione e le colonne con i nomi di piattaforma.

|Nome configurazione|Piattaforma: Win32|Piattaforma: Win64|
|------------------------|----------------------|----------------------|
|*Debug*|\<Eseguire il debug delle impostazioni Win32>|\<Eseguire il debug delle impostazioni Win64>|
|*Rilascio*|\<Rilasciare le impostazioni Win32>|\<Rilasciare le impostazioni Win64>|
|*MyConfig (configurazione in stato di in*|N/D|\<Impostazioni Win64 myConfig>|

> [!NOTE]
> Non è possibile creare una configurazione di soluzione *MyConfig* che esclude una piattaforma Win32 a meno che il progetto di destinazione non supporti Win32.

 La modifica della configurazione attiva per una soluzione seleziona il set di configurazioni di progetto compilate, eseguite, sottoposte a debug o distribuite in tale soluzione. Ad esempio, se si modifica la configurazione della soluzione attiva da *Release* a *Debug*, tutti i progetti all'interno di tale soluzione vengono compilati automaticamente con la configurazione dei progetti indicata nella configurazione di debug della soluzione. Le configurazioni dei progetti sono denominate Debug, *a* meno che l'utente non abbia apportato modifiche manuali in Configuration Manager dell'ambiente.

 Le proprietà di configurazione della soluzione archiviate per ogni progetto includono il nome del progetto, il nome della configurazione del progetto, i flag per indicare se compilare o meno e il nome della piattaforma. Per ulteriori informazioni, vedere [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

 L'utente può visualizzare e impostare i parametri di configurazione della soluzione selezionando la soluzione nella gerarchia (Esplora soluzioni) e aprendo le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione del progetto selezionando un progetto in Esplora soluzioni e aprendo le pagine delle proprietà per tale progetto.

 L'utente può anche compilare un progetto utilizzando le impostazioni di configurazione di rilascio e tutto il resto con le impostazioni di configurazione di debug, se necessario. Per ulteriori informazioni, consultate [Configurazione del progetto per la compilazione.](../../extensibility/internals/project-configuration-for-building.md)

 Nel diagramma seguente viene illustrato come vengono implementate le interfacce che supportano le configurazioni di soluzione e progetto:The following diagram shows how the interfaces that support solution and project configurations are implemented:

 ![Grafico delle interfacce](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces (informazioni in lingua lingua inlinguata in") di configurazione Interfacce di configurazione

 Alcune note relative al diagramma precedente:

- `IDispatch`è contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo avere le interfacce di configurazione nell'oggetto Sfoglia.

- `IVsDebuggableProjectCfg`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è obbligatorio per il supporto del debug.

- `IVsProjectCfg2`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del raggruppamento di output.

- L'oggetto Provider di configurazione è contrassegnato come oggetto facoltativo, ma l'opzione è la posizione in cui implementarlo. È possibile implementare l'oggetto nell'oggetto del progetto o su un oggetto separato.

- `IVsCfgProvider2`è necessario per il supporto della piattaforma e la modifica della configurazione. `IVsCfgProvider`è sufficiente se non si implementa tale funzionalità.

- Alcuni di questi oggetti illustrati nel diagramma come oggetti separati possono essere combinati nella stessa classe in cui pratico in base ai requisiti di progettazione specifici. In altri argomenti di questa sezione, tuttavia, gli oggetti e le interfacce associati a tali oggetti verranno illustrati in base allo scenario presentato nel diagramma.

- Alcuni oggetti vengono implementati separatamente. Ad esempio, la compilazione di progetti e soluzioni si verificano in thread separati e l'oggetto per gestire la compilazione si verifica separatamente dall'oggetto che descrive la configurazione per la compilazione.

  Per ulteriori informazioni sulle interfacce degli oggetti di configurazione e sulle interfacce del provider di configurazione nel diagramma precedente, vedere [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md). Inoltre, la configurazione di Project per la [compilazione](../../extensibility/internals/project-configuration-for-building.md) fornisce ulteriori informazioni sul generatore di configurazione e le interfacce degli oggetti di dipendenza di compilazione e la [configurazione di progetto per la gestione](../../extensibility/internals/project-configuration-for-managing-deployment.md) della distribuzione descrive ulteriormente le interfacce associate al deployer della configurazione e agli oggetti dipendenza di distribuzione. Infine, la configurazione di [Project per l'output](../../extensibility/internals/project-configuration-for-output.md) descrive il gruppo di output e le interfacce degli oggetti di output e l'utilizzo delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configurazione del progetto per la creazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
