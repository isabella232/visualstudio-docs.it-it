---
title: Panoramica sulle opzioni di configurazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 791c50e6839190fa3700c335896f24f0714a64bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415147"
---
# <a name="configuration-options-overview"></a>Panoramica sulle opzioni di configurazione
I progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può supportare più configurazioni che possono essere compilate, sottoposto a debug, esecuzione e/o distribuita. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà, in genere le opzioni del compilatore e percorsi dei file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni *Debug* e *rilascio*. Queste configurazioni possono essere applicate con le relative impostazioni predefinite, o modificata per soddisfare i requisiti di progetto e/o soluzioni specifici. Alcuni pacchetti possono essere compilati in due modi: come editor ActiveX o come un componente sul posto. I progetti non sono necessario supportare più configurazioni, tuttavia. Se è disponibile solo una configurazione, tale configurazione viene mappata in tutte le configurazioni di soluzione.

 Le configurazioni in genere sono costituiti da due parti: il nome della configurazione (ad esempio *eseguire il Debug* o *rilascio*) e le impostazioni della piattaforma. Nome della piattaforma di una configurazione identifica l'ambiente che impostare destinazioni di configurazione, ad esempio un'API o la piattaforma del sistema operativo. Gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è possibile creare una piattaforma; devono scegliere le selezioni un progetto VSPackage consente. Quando un utente installa un pacchetto VSPackage, la piattaforma di distribuzione creata durante lo sviluppo del pacchetto si può verificare qualsiasi nome di piattaforma desiderato in base eventuali criteri impostati dal creatore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme resi disponibili tramite il pacchetto VSPackage quando viene creata un'istanza le pagine delle proprietà.

 Nomi di piattaforma sono facoltativi, poiché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non dispone di un nome di piattaforma, la stringa **n/d** viene visualizzato nell'interfaccia utente.

 Ogni soluzione ha un proprio set di configurazioni, solo uno dei quali può essere attivo contemporaneamente. Una configurazione di soluzione è un set di non più di una configurazione di ogni progetto. Il criterio "non più di" fa è dovuto l'opzione per escludere un progetto da una configurazione di soluzione. Gli utenti possono creare le proprie configurazioni soluzione personalizzata.

 La tabella seguente illustra la configurazione di configurazioni tipiche per un progetto. Le righe sono contrassegnate con nomi di configurazione e le colonne con nomi di piattaforma.

|Nome della configurazione|Piattaforma: Win32|Piattaforma: Win64|
|------------------------|----------------------|----------------------|
|*Debug*|\<Eseguire il debug Win32 Impostazioni >|\<Eseguire il debug Win64 Impostazioni >|
|*Rilascio*|\<Impostazioni di Win32 versione >|\<Impostazioni Win64 versione >|
|*MyConfig*|N/D|\<Impostazioni MyConfig Win64 >|

> [!NOTE]
> Non è possibile creare un *MyConfig* configurazione della soluzione che esclude una piattaforma di Win32, a meno che il progetto di destinazione non supporta Win32.

 Modifica la configurazione attiva per una soluzione consente di selezionare il set di configurazioni di progetto viene compilato, eseguire, eseguire il debug o distribuito in tale soluzione. Ad esempio, se si modifica la configurazione soluzione attiva da *Release* a *Debug*, tutti i progetti all'interno della soluzione vengono creati automaticamente con la configurazione del progetto indicato nel configurazione di debug della soluzione. Le configurazioni di progetto sono detti anche *Debug* , a meno che l'utente ha apportato modifiche manuali dell'ambiente di Configuration Manager.

 Le proprietà di configurazione di soluzione archiviate per ogni progetto includono il nome del progetto, nome configurazione di progetto, i flag per indicare se per compilare o distribuire e nome della piattaforma. Per altre informazioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).

 L'utente può visualizzare e impostare i parametri di configurazione di soluzione, selezionando la soluzione della gerarchia (Esplora soluzioni) e aprire le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione di progetto, selezionare un progetto in Esplora soluzioni e aprire le pagine delle proprietà per il progetto.

 L'utente può anche compilare un progetto con le impostazioni di configurazione di versione e tutte le altre impostazioni di configurazione di debug se necessario. Per altre informazioni, vedere [configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).

 Il diagramma seguente illustra come vengono implementate le interfacce che supportano le configurazioni di soluzione e progetto:

 ![Rappresentazione grafica delle interfacce di configurazione](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") interfacce di configurazione

 Alcune note relative al diagramma precedente:

- `IDispatch` viene contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo per disporre le interfacce di configurazione nell'oggetto di visualizzazione.

- `IVsDebuggableProjectCfg` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del debug.

- `IVsProjectCfg2` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per l'output di supporto di raggruppamento.

- L'oggetto Provider di configurazione è contrassegnato come un oggetto facoltativo, ma l'opzione è la posizione in cui implementarla. È possibile implementare l'oggetto sull'oggetto progetto o in un oggetto separato.

- `IVsCfgProvider2` è necessaria per il supporto di piattaforma e la modifica della configurazione. `IVsCfgProvider` è sufficiente se non si implementa questa funzionalità.

- Alcuni di questi oggetti illustrati nel diagramma come oggetti separati possono essere combinati nella stessa classe dove possibile. in base alle esigenze specifiche di progettazione. In altri argomenti di questa sezione, tuttavia, gli oggetti e interfacce associate a tali oggetti verranno analizzate in base allo scenario presentato nel diagramma.

- Alcuni oggetti vengono implementate separatamente. Ad esempio, progetto e soluzione compilazione si verificano su thread separati e l'oggetto per la gestione della qualità della vita compilazione separatamente dall'oggetto che descrive la configurazione per la compilazione.

  Per altre informazioni sulle interfacce dell'oggetto di configurazione e le interfacce di oggetti provider di configurazione nel diagramma precedente, vedere [oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md). È inoltre [configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md) disponibili ulteriori informazioni sulla dipendenza configurazione generatore e compilare interfacce dell'oggetto, e [configurazione del progetto per la Gestione distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md) Descrive ulteriormente le interfacce collegate ai distributori di configurazione e gli oggetti di dipendenza di distribuzione. Infine [configurazione del progetto per l'output](../../extensibility/internals/project-configuration-for-output.md) descrive il gruppo di output e output interfacce dell'oggetto e l'uso delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Configurazione della soluzione](../../extensibility/internals/solution-configuration.md)