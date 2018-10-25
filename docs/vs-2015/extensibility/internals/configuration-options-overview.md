---
title: Panoramica sulle opzioni di configurazione | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e502f78698d830c916b09968e8fa2cfbcd74fbf7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915776"
---
# <a name="configuration-options-overview"></a>Panoramica delle opzioni di configurazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I progetti in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] può supportare più configurazioni che possono essere compilate, sottoposto a debug, esecuzione e/o distribuita. Una configurazione è un tipo di compilazione descritto con un set denominato di proprietà, in genere le opzioni del compilatore e percorsi dei file. Per impostazione predefinita, le nuove soluzioni contengono due configurazioni, Debug e rilascio. Queste configurazioni possono essere applicate con le relative impostazioni predefinite, o modificata per soddisfare i requisiti di progetto e/o soluzioni specifici. Alcuni pacchetti possono essere compilati in due modi: come editor ActiveX o come un componente sul posto. I progetti non sono necessario supportare più configurazioni, tuttavia. Se è disponibile solo una configurazione, tale configurazione viene mappata in tutte le configurazioni di soluzione.  
  
 Le configurazioni in genere sono costituiti da due parti, ovvero il nome della configurazione (ad esempio Debug o Release) e le impostazioni di piattaforma. Nome della piattaforma di una configurazione identifica l'ambiente che impostare destinazioni di configurazione, ad esempio un'API o la piattaforma del sistema operativo. Gli utenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non è possibile creare una piattaforma; devono scegliere le selezioni un progetto VSPackage consente. Quando un utente installa un pacchetto VSPackage, la piattaforma di distribuzione creata durante lo sviluppo del pacchetto si può verificare qualsiasi nome di piattaforma desiderato in base eventuali criteri impostati dal creatore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme resi disponibili tramite il pacchetto VSPackage quando viene creata un'istanza le pagine delle proprietà.  
  
 Nomi di piattaforma sono facoltativi, poiché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non dispone di un nome di piattaforma, la stringa "n/d" viene visualizzato nell'interfaccia utente.  
  
 Ogni soluzione ha un proprio set di configurazioni, solo uno dei quali può essere attivo contemporaneamente. Una configurazione di soluzione è un set di non più di una configurazione di ogni progetto. Il criterio "non più di" fa è dovuto l'opzione per escludere un progetto da una configurazione di soluzione. Gli utenti possono creare le proprie configurazioni soluzione personalizzata.  
  
 La tabella seguente illustra la configurazione di configurazioni tipiche per un progetto. Le righe sono contrassegnate con nomi di configurazione e le colonne con nomi di piattaforma.  
  
|Nome della configurazione|Piattaforma: Win32|Piattaforma: Win64|  
|------------------------|----------------------|----------------------|  
|Debug|\<Eseguire il debug Win32 Impostazioni >|\<Eseguire il debug Win64 Impostazioni >|  
|Rilascio|\<Impostazioni di Win32 versione >|\<Impostazioni Win64 versione >|  
|MyConfig|N/D|\<Impostazioni MyConfig Win64 >|  
  
> [!NOTE]
>  È possibile creare una configurazione di soluzione "MyConfig" che esclude una piattaforma "Win32", a meno che il progetto di destinazione non supporta Win32.  
  
 Modifica la configurazione attiva per una soluzione consente di selezionare il set di configurazioni di progetto che vengono compilate, eseguire, eseguire il debug o distribuito in tale soluzione. Ad esempio, se si modifica la configurazione soluzione attiva da Release a Debug, tutti i progetti all'interno della soluzione vengono compilati automaticamente con la configurazione del progetto indicato nella configurazione di Debug della soluzione. Le configurazioni di progetto sono in genere anche denominata Debug a meno che l'utente ha apportato modifiche manuali dell'ambiente di Configuration Manager.  
  
 Le proprietà di configurazione di soluzione archiviate per ogni progetto includono il nome del progetto, nome configurazione di progetto, i flag per indicare se per compilare o distribuire e nome della piattaforma. Per altre informazioni, vedere [configurazione della soluzione](../../extensibility/internals/solution-configuration.md).  
  
 L'utente può visualizzare e impostare i parametri di configurazione di soluzione, selezionando la soluzione della gerarchia (Esplora soluzioni) e aprire le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione di progetto, selezionare un progetto in Esplora soluzioni e aprire le pagine delle proprietà per il progetto.  
  
 L'utente può anche compilare un progetto con le impostazioni di configurazione di versione e tutte le altre impostazioni di configurazione di Debug se necessario. Per altre informazioni, vedere [configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md).  
  
 Il diagramma seguente illustra come vengono implementate le interfacce che supportano le configurazioni di soluzione e progetto:  
  
 ![Rappresentazione grafica delle interfacce di configurazione](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfacce di configurazione  
  
 Alcune note relative al diagramma precedente:  
  
- `IDispatch` è contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo per disporre le interfacce di configurazione nell'oggetto di visualizzazione.  
  
- `IVsDebuggableProjectCfg` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del debug.  
  
- `IVsProjectCfg2` è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per l'output di supporto di raggruppamento.  
  
- Il `Config Provider` oggetto è contrassegnato come un oggetto facoltativo, ma l'opzione è la posizione in cui implementarla. È possibile implementare l'oggetto sull'oggetto progetto o in un oggetto separato.  
  
- `IVsCfgProvider2` è necessaria per il supporto di piattaforma e la modifica della configurazione. `IVsCfgProvider` è sufficiente se non si implementa questa funzionalità.  
  
- Alcuni di questi oggetti illustrati nel diagramma come oggetti separati possono essere combinati nella stessa classe dove possibile. in base alle esigenze specifiche di progettazione. In altri argomenti di questa sezione, tuttavia, gli oggetti e interfacce associate a tali oggetti verranno analizzate in base allo scenario presentato nel diagramma.  
  
- Alcuni oggetti vengono implementate separatamente. Ad esempio, progetto e soluzione compilazione si verificano su thread separati e l'oggetto per la gestione della qualità della vita compilazione separatamente dall'oggetto che descrive la configurazione per la compilazione.  
  
  Per altre informazioni sulle interfacce dell'oggetto di configurazione e le interfacce di oggetto Provider di configurazione nel diagramma precedente, vedere [oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md). Inoltre, [configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md) fornisce altre informazioni sulle interfacce di generatore di configurazione e l'oggetto di dipendenza di compilazione, e [configurazione del progetto per la Gestione distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md) Descrive ulteriormente le interfacce collegate ai distributori di configurazione e gli oggetti di dipendenza di distribuzione. Infine [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md) descrive le interfacce del gruppo di Output e l'oggetto di Output e l'utilizzo delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione di soluzioni](../../extensibility/internals/solution-configuration.md)

