---
title: Panoramica delle opzioni di configurazione | Microsoft Docs
description: Informazioni sulle opzioni per le configurazioni di progetto in Visual Studio. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà e percorsi di file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa018d340e016ba5c9f424f705599a150ecdc818
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884689"
---
# <a name="configuration-options-overview"></a>Panoramica delle opzioni di configurazione
I progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono supportare più configurazioni che possono essere compilate, sottoposte a debug, eseguite e/o distribuite. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà, in genere le opzioni del compilatore e i percorsi dei file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni, *debug* e *Release*. Queste configurazioni possono essere applicate usando le impostazioni predefinite o modificate per soddisfare i requisiti specifici della soluzione e/o del progetto. Alcuni pacchetti possono essere compilati in due modi: come editor ActiveX o come componente sul posto. I progetti non devono tuttavia supportare più configurazioni. Se è disponibile una sola configurazione, viene eseguito il mapping di tale configurazione a tutte le configurazioni della soluzione.

 Le configurazioni sono in genere costituite da due parti: il nome della configurazione (ad esempio *debug* o *Release*) e le impostazioni della piattaforma. Il nome della piattaforma di una configurazione identifica l'ambiente di destinazione della configurazione, ad esempio un set di API o una piattaforma del sistema operativo. Gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non possono creare una piattaforma, ma devono scegliere tra le selezioni consentite da un pacchetto VSPackage di progetto. Quando un utente installa un pacchetto VSPackage, la piattaforma di recapito creata durante lo sviluppo del pacchetto può rendere visibile qualsiasi nome di piattaforma desiderato in base ai criteri impostati dall'autore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme rese disponibili tramite il pacchetto VSPackage quando viene creata un'istanza delle pagine delle proprietà.

 I nomi di piattaforma sono facoltativi perché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non dispone di un nome di piattaforma, la stringa **N/a** viene visualizzata nell'interfaccia utente.

 Ogni soluzione dispone di un proprio set di configurazioni, solo una delle quali può essere attiva alla volta. Una configurazione della soluzione è un set di non più di una configurazione di ogni progetto. La clausola "non più di" è causata dall'opzione di esclusione di un progetto da una configurazione di soluzione. Gli utenti possono creare configurazioni di soluzioni personalizzate.

 Nella tabella seguente viene illustrata la configurazione tipica delle configurazioni per un progetto. Le righe vengono etichettate con i nomi di configurazione e le colonne con nomi di piattaforma.

|Nome configurazione|Piattaforma: Win32|Piattaforma: Win64|
|------------------------|----------------------|----------------------|
|*Eseguire il debug*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Rilascio*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|N/D|\<MyConfig Win64 settings>|

> [!NOTE]
> Non è possibile creare una configurazione *della soluzione di configurazione che* escluda una piattaforma Win32, a meno che il progetto di destinazione non supporti Win32.

 Modificando la configurazione attiva per una soluzione, viene selezionato il set di configurazioni di progetto compilato, eseguito, sottoposto a debug o distribuito nella soluzione. Se ad esempio si modifica la configurazione della soluzione attiva da *Release* a *debug*, tutti i progetti all'interno della soluzione vengono compilati automaticamente con la configurazione dei progetti indicata nella configurazione di debug della soluzione. Anche le configurazioni dei progetti sono denominate *debug* , a meno che l'utente non abbia apportato modifiche manuali all'Configuration Manager dell'ambiente.

 Le proprietà di configurazione della soluzione archiviate per ogni progetto includono il nome del progetto, il nome della configurazione del progetto, i flag per indicare se compilare o meno la compilazione o la distribuzione e il nome della piattaforma. Per altre informazioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

 L'utente può visualizzare e impostare i parametri di configurazione della soluzione selezionando la soluzione nella gerarchia (Esplora soluzioni) e aprendo le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione del progetto selezionando un progetto in Esplora soluzioni e aprendo le pagine delle proprietà per il progetto.

 L'utente può anche compilare un progetto usando le impostazioni di configurazione della versione e tutte le altre con le impostazioni di configurazione di debug, se necessario. Per ulteriori informazioni, vedere [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).

 Il diagramma seguente illustra il modo in cui vengono implementate le interfacce che supportano le configurazioni della soluzione e del progetto:

 ![Rappresentazione grafica delle interfacce di configurazione](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfacce di configurazione

 Alcune note relative al diagramma precedente:

- `IDispatch` è contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo avere le interfacce di configurazione nell'oggetto browse.

- `IVsDebuggableProjectCfg` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del debug.

- `IVsProjectCfg2` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del raggruppamento di output.

- L'oggetto provider di configurazione è contrassegnato come oggetto facoltativo, ma l'opzione è la posizione in cui implementarla. È possibile implementare l'oggetto nell'oggetto progetto o in un oggetto separato.

- `IVsCfgProvider2` è necessario per il supporto della piattaforma e la modifica della configurazione. `IVsCfgProvider` è sufficiente se non si implementa tale funzionalità.

- Alcuni di questi oggetti illustrati nel diagramma come oggetti separati possono essere combinati nella stessa classe in cui sono pratici in base ai requisiti di progettazione specifici. Negli altri argomenti di questa sezione, tuttavia, gli oggetti e le interfacce associate a tali oggetti verranno discussi in base allo scenario presentato nel diagramma.

- Determinati oggetti vengono implementati separatamente. Ad esempio, la compilazione di progetti e soluzioni si verifica su thread separati e l'oggetto per gestire la compilazione si trova separatamente dall'oggetto che descrive la configurazione per la compilazione.

  Per ulteriori informazioni sulle interfacce degli oggetti di configurazione e le interfacce degli oggetti del provider di configurazione nel diagramma precedente, vedere [oggetto configurazione progetto](../../extensibility/internals/project-configuration-object.md). Inoltre, la [configurazione di progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md) fornisce ulteriori informazioni sulle interfacce generatore di configurazione e oggetto dipendenza compilazione e la [configurazione del progetto per la gestione della distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md) descrive ulteriormente le interfacce associate al deployer di configurazione e agli oggetti dipendenza della distribuzione. Infine, la [configurazione di progetto per l'output](../../extensibility/internals/project-configuration-for-output.md) descrive le interfacce del gruppo di output e dell'oggetto di output e l'utilizzo delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
