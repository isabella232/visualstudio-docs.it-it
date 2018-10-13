---
title: Configurazione della soluzione | Microsoft Docs
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
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2efd5a626e92d180f7c842172f764fa7f8011e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245798"
---
# <a name="solution-configuration"></a>Configurazione soluzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Configurazioni soluzione archiviano proprietà a livello di soluzione. Quindi indirizzano il comportamento dei **avviare** chiave (F5) e **compilazione** comandi. Per impostazione predefinita, questi comandi compilare e avviare la configurazione di debug. Entrambi i comandi vengono eseguite nel contesto di una configurazione di soluzione. Ciò significa che l'utente può aspettarsi F5 per avviare e qualunque sia la soluzione attiva viene configurata tramite le impostazioni di compilazione. L'ambiente è progettato per ottimizzare per le soluzioni anziché per i progetti quando si tratta di compilazione e l'esecuzione.  
  
 Barra degli strumenti standard di Visual Studio contiene un pulsante di avvio e un elenco a discesa a destra del pulsante Avvia configurazione della soluzione. Questo elenco consente agli utenti di scegliere la configurazione da avviare quando viene premuto F5, creare le proprie configurazioni di soluzione o modificare una configurazione esistente.  
  
> [!NOTE]
>  Non sono presenti interfacce di estendibilità per creare o modificare le configurazioni di soluzione. È necessario usare `DTE.SolutionBuilder`. Tuttavia, esistono API di estendibilità per la gestione della compilazione della soluzione. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.  
  
 Ecco come è possibile implementare le configurazioni di soluzione supportate dal tipo di progetto:  
  
-   Progetto  
  
     Visualizza i nomi dei progetti inclusi nella soluzione corrente.  
  
-   Configurazione  
  
     Per fornire l'elenco delle configurazioni supportate per il tipo di progetto e visualizzato nelle pagine delle proprietà, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.  
  
     La colonna di configurazione viene visualizzato il nome della configurazione del progetto per compilare in questa configurazione di soluzione ed elenca tutte le configurazioni di progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della configurazione, nuovo o modifica selezioni vengono anche visualizzate sotto l'intestazione di configurazione. Ognuna di queste impostazioni avviare le finestre di dialogo che chiamano metodi del `IVsCfgProvider2` interfaccia per modificare le configurazioni del progetto.  
  
     Se un progetto non supporta le configurazioni, la colonna di configurazione viene visualizzato Nessuno ed è disabilitata.  
  
-   Piattaforma  
  
     Consente di visualizzare la piattaforma consente di compilare per la configurazione di progetto selezionato ed elenca tutte le piattaforme disponibili per il progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della piattaforma, nuovo o modifica selezioni vengono anche visualizzate sotto l'intestazione della piattaforma. Ognuna di queste impostazioni avviare le finestre di dialogo chiamano `IVsCfgProvider2` metodi per modificare le piattaforme disponibili del progetto.  
  
     Se un progetto non supporta le piattaforme, la colonna di piattaforma per il progetto viene visualizzato Nessuno ed è disabilitata.  
  
-   Compilazione  
  
     Specifica se il progetto è compilato dalla configurazione della soluzione corrente. I progetti non selezionati non vengono compilati quando vengono richiamati i comandi di compilazione a livello di soluzione nonostante eventuali dipendenze di progetto che contengono. Progetti non selezionati da compilare sono ancora inclusi nel debug, esecuzione, creazione di pacchetti e distribuzione della soluzione.  
  
-   Distribuzione  
  
     Specifica se il progetto verrà distribuito quando vengono utilizzati i comandi di avvio o distribuire con la configurazione di compilazione della soluzione selezionata. La casella di controllo per questo campo sarà disponibile se il progetto supporta la distribuzione mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia sul relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> oggetto.  
  
 Dopo avere aggiunto una nuova configurazione di soluzione, l'utente può selezionarlo dall'elenco a discesa Configurazione della soluzione nella barra degli strumenti standard per compilare e/o che la configurazione di avvio.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)

