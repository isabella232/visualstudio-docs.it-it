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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0bde8342961136cddf5a89bb5799abacef462e5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028969"
---
# <a name="configuration-options-overview"></a>Panoramica delle opzioni di configurazione
I progetti in possono supportare più configurazioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che possono essere compilate, di cui è possibile eseguire il debug, l'esecuzione e/o la distribuzione. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà, in genere opzioni del compilatore e percorsi di file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni, *Debug* *e Rilascio.* Queste configurazioni possono essere applicate usando le impostazioni predefinite o modificate per soddisfare i requisiti specifici della soluzione e/o del progetto. Alcuni pacchetti possono essere compilati in due modi: come editor ActiveX o come componente sul posto. Non è tuttavia necessario che i progetti supportino più configurazioni. Se è disponibile una sola configurazione, tale configurazione viene mappata a tutte le configurazioni della soluzione.

 Le configurazioni sono in genere costituite da due parti: il nome della configurazione ( ad esempio *Debug* *o Versione*) e le impostazioni della piattaforma. Il nome della piattaforma di una configurazione identifica l'ambiente di destinazione della configurazione, ad esempio un set di API o una piattaforma del sistema operativo. Gli utenti di non possono creare una piattaforma, ma devono scegliere tra le selezioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di un progetto che IL PACCHETTO VSPackage consente. Quando un utente installa un VSPackage, la piattaforma di distribuzione creata durante lo sviluppo del pacchetto può visualizzare qualsiasi nome di piattaforma desiderato in base a qualsiasi criterio impostato dall'autore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme rese disponibili tramite il pacchetto VSPackage quando viene creata un'istanza delle pagine delle proprietà.

 I nomi delle piattaforme sono facoltativi perché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non ha un nome di piattaforma, nell'interfaccia utente viene visualizzata la stringa **N/D.**

 Ogni soluzione ha un proprio set di configurazioni, di cui solo una può essere attiva alla volta. Una configurazione della soluzione è un set di non più di una configurazione da ogni progetto. La clausola "non più di" è dovuta alla possibilità di escludere un progetto da una configurazione della soluzione. Gli utenti possono creare configurazioni di soluzione personalizzate.

 La tabella seguente illustra la configurazione tipica delle configurazioni per un progetto. Le righe sono etichettate con i nomi di configurazione e le colonne con i nomi della piattaforma.

|Nome configurazione|Piattaforma: Win32|Piattaforma: Win64|
|------------------------|----------------------|----------------------|
|*Eseguire il debug*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Rilascio*|\<Release Win32 settings>|\<Release Win64 settings>|
|*MyConfig*|N/A|\<MyConfig Win64 settings>|

> [!NOTE]
> Non è possibile creare *una configurazione della soluzione MyConfig* che esclude una piattaforma Win32 a meno che il progetto di destinazione non supporti Win32.

 La modifica della configurazione attiva per una soluzione consente di selezionare il set di configurazioni di progetto compilate, eseguite, di cui è stato eseguito il debug o distribuite in tale soluzione. Ad esempio, se si modifica  la configurazione della soluzione attiva da Versione a Debug *,* tutti i progetti all'interno di tale soluzione vengono compilati automaticamente con la configurazione dei progetti indicata nella configurazione di debug della soluzione. Le configurazioni dei progetti sono denominate anche *Debug,* a meno che l'utente non abbia apportato modifiche manuali nella configurazione dell'ambiente Gestione configurazione.

 Le proprietà di configurazione della soluzione archiviate per ogni progetto includono il nome del progetto, il nome della configurazione del progetto, i flag per indicare se compilare o distribuire e il nome della piattaforma. Per altre informazioni, vedere [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

 L'utente può visualizzare e impostare i parametri di configurazione della soluzione selezionando la soluzione nella gerarchia (Esplora soluzioni) e aprendo le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione del progetto selezionando un progetto in Esplora soluzioni e aprendo le pagine delle proprietà per tale progetto.

 L'utente può anche compilare un progetto usando le impostazioni di configurazione della versione e tutto il resto con le impostazioni di configurazione di debug, se necessario. Per altre informazioni, vedere configurazione [Project per la compilazione di](../../extensibility/internals/project-configuration-for-building.md).

 Il diagramma seguente illustra come vengono implementate le interfacce che supportano le configurazioni di soluzioni e progetti:

 ![Immagine delle interfacce di configurazione](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfacce di configurazione

 Alcune note relative al diagramma precedente:

- `IDispatch` è contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo avere le interfacce di configurazione nell'oggetto browse.

- `IVsDebuggableProjectCfg` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del debug.

- `IVsProjectCfg2` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del raggruppamento di output.

- L'oggetto provider di configurazione è contrassegnato come oggetto facoltativo, ma l'opzione è la posizione in cui implementarlo. È possibile implementare l'oggetto nell'oggetto di progetto o in un oggetto separato.

- `IVsCfgProvider2` è necessario per il supporto della piattaforma e la modifica della configurazione. `IVsCfgProvider` è sufficiente se non si implementa tale funzionalità.

- Alcuni di questi oggetti illustrati nel diagramma come oggetti separati possono essere combinati nella stessa classe in cui è pratica in base ai requisiti di progettazione specifici. In altri argomenti di questa sezione, tuttavia, gli oggetti e le interfacce associati a tali oggetti verranno illustrati in base allo scenario presentato nel diagramma.

- Alcuni oggetti vengono implementati separatamente. Ad esempio, la compilazione di progetti e soluzioni si verifica in thread separati e l'oggetto per gestire la compilazione risiede separatamente dall'oggetto che descrive la configurazione per la compilazione.

  Per altre informazioni sulle interfacce degli oggetti di configurazione e sulle interfacce degli oggetti del provider di configurazione nel [diagramma precedente,](../../extensibility/internals/project-configuration-object.md)vedere Project configuration object . Inoltre, [](../../extensibility/internals/project-configuration-for-building.md) la configurazione Project per la compilazione fornisce altre informazioni su Configuration Builder e sulle interfacce degli oggetti dipendenza di compilazione e la configurazione [di Project](../../extensibility/internals/project-configuration-for-managing-deployment.md) per la gestione della distribuzione descrive ulteriormente le interfacce associate agli oggetti di distribuzione della configurazione e alle dipendenze di distribuzione. Infine, Project configurazione per [l'output](../../extensibility/internals/project-configuration-for-output.md) descrive le interfacce del gruppo di output e degli oggetti di output e l'uso delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Project configurazione per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)
