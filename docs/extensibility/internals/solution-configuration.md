---
title: Configurazione della soluzione - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705382"
---
# <a name="solution-configuration"></a>Configurazione soluzione
Le configurazioni della soluzione archiviano le proprietà a livello di soluzione. Indirizzano il comportamento dei comandi **Start** (F5) e **Build.** Per impostazione predefinita, questi comandi compilano e avviano la configurazione di debug. Entrambi i comandi vengono eseguiti nel contesto di una configurazione di soluzione. Ciò significa che l'utente può aspettarsi F5 per avviare e compilare qualsiasi soluzione attiva è configurata tramite le impostazioni. L'ambiente è progettato per ottimizzare le soluzioni anziché i progetti quando si tratta di compilazione ed esecuzione.

 La barra degli strumenti standard di Visual Studio contiene un pulsante Start e un elenco a discesa di configurazione della soluzione a destra del pulsante Start. Questo elenco consente agli utenti di scegliere la configurazione da iniziare quando si preme F5, creare configurazioni di soluzione personalizzate o modificare una configurazione esistente.

> [!NOTE]
> Non sono disponibili interfacce di estensibilità per creare o modificare le configurazioni della soluzione. È necessario utilizzare `DTE.SolutionBuild`. Tuttavia, esistono API di estendibilità per la gestione della compilazione della soluzione. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Ecco come implementare le configurazioni di soluzione supportate dal tipo di progetto:Here is how you can implement the solution configurations supported by your project type:

- Project

   Visualizza i nomi dei progetti trovati nella soluzione corrente.

- Configurazione

   Per fornire l'elenco delle configurazioni supportate dal tipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>di progetto e visualizzate nelle pagine delle proprietà, implementare .

   Nella colonna Configurazione viene visualizzato il nome della configurazione di progetto da compilare in questa configurazione di soluzione ed elencate tutte le configurazioni di progetto quando si fa clic sul pulsante freccia. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> chiama il metodo per compilare questo elenco. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> il metodo indica che il progetto supporta la modifica della configurazione, le selezioni Nuovo o Modifica vengono visualizzate anche sotto l'intestazione Configurazione. Ognuna di queste selezioni avvia finestre `IVsCfgProvider2` di dialogo che chiamano i metodi dell'interfaccia per modificare le configurazioni del progetto.

   Se un progetto non supporta le configurazioni, nella colonna Configurazione viene visualizzato Nessuno ed è disabilitato.

- Piattaforma

   Visualizza la piattaforma per cui viene compilata la configurazione del progetto selezionata ed elenca tutte le piattaforme disponibili per il progetto quando si fa clic sul pulsante freccia. L'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> chiama il metodo per compilare questo elenco. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> il metodo indica che il progetto supporta la modifica della piattaforma, le selezioni Nuovo o Modifica vengono visualizzate anche sotto l'intestazione Piattaforma. Ognuna di queste selezioni avvia `IVsCfgProvider2` finestre di dialogo che chiamano i metodi per modificare le piattaforme disponibili del progetto.

   Se un progetto non supporta le piattaforme, nella colonna della piattaforma del progetto viene visualizzato None ed è disabilitato.

- Compilazione

   Specifica se il progetto viene compilato o meno dalla configurazione della soluzione corrente. I progetti non selezionati non vengono compilati quando i comandi di compilazione a livello di soluzione vengono richiamati nonostante le dipendenze di progetto che contengono. I progetti non selezionati per essere compilati sono ancora inclusi nel debug, nell'esecuzione, nella creazione di pacchetti e nella distribuzione della soluzione.

- Distribuire

   Specifica se il progetto verrà distribuito o meno quando i comandi Start o Deploy vengono utilizzati con la configurazione di compilazione della soluzione selezionata. La casella di controllo per questo campo sarà disponibile se <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> progetto supporta la distribuzione implementando l'interfaccia sul relativo oggetto.

  Dopo aver aggiunto una nuova configurazione di soluzione, l'utente può selezionarla dalla casella di riepilogo a discesa Configurazione soluzione sulla barra degli strumenti standard per compilare e/o avviare tale configurazione.

## <a name="see-also"></a>Vedere anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
