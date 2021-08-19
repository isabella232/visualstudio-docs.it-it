---
title: Configurazione della soluzione | Microsoft Docs
description: Informazioni su come implementare le configurazioni della soluzione supportate dal tipo di progetto, che indirizzano il comportamento dei comandi Start (F5) e Build.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ecd5d2fc6fba5d42b2c9435f47b371dd5ca346f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117683"
---
# <a name="solution-configuration"></a>Configurazione soluzione
Le configurazioni di soluzione archiviano le proprietà a livello di soluzione. Indirizzano il comportamento dei **comandi Start** (F5) e **Build.** Per impostazione predefinita, questi comandi compilano e avviano la configurazione di debug. Entrambi i comandi vengono eseguiti nel contesto di una configurazione della soluzione. Ciò significa che l'utente può aspettarsi che F5 inizi e compilare qualsiasi soluzione attiva sia configurata tramite le impostazioni. L'ambiente è progettato per ottimizzare le soluzioni anziché i progetti quando si tratta di compilazione ed esecuzione.

 La barra Visual Studio standard contiene un pulsante Start e un elenco a discesa di configurazione della soluzione a destra del pulsante Start. Questo elenco consente agli utenti di scegliere la configurazione da iniziare quando si preme F5, creare configurazioni di soluzione personalizzate o modificare una configurazione esistente.

> [!NOTE]
> Non sono disponibili interfacce di estendibilità per creare o modificare le configurazioni della soluzione. È necessario utilizzare `DTE.SolutionBuild`. Esistono tuttavia API di estendibilità per la gestione della compilazione della soluzione. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Ecco come implementare le configurazioni della soluzione supportate dal tipo di progetto:

- Project

   Visualizza i nomi dei progetti trovati nella soluzione corrente.

- Configurazione

   Per fornire l'elenco delle configurazioni supportate dal tipo di progetto e visualizzate nelle pagine delle proprietà, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   La colonna Configurazione visualizza il nome della configurazione del progetto da compilare in questa configurazione della soluzione ed elenca tutte le configurazioni del progetto quando si fa clic sul pulsante freccia. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> il metodo per compilare questo elenco. Se il metodo indica che il progetto supporta la modifica della configurazione, vengono visualizzate anche le selezioni Nuovo o Modifica <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> sotto l'intestazione Configurazione. Ognuna di queste selezioni avvia finestre di dialogo che chiamano metodi `IVsCfgProvider2` dell'interfaccia per modificare le configurazioni del progetto.

   Se un progetto non supporta le configurazioni, la colonna Configurazione visualizza Nessuna ed è disabilitata.

- Piattaforma

   Visualizza la piattaforma per cui vengono compilate le configurazioni del progetto selezionate ed elenca tutte le piattaforme disponibili per il progetto quando si fa clic sul pulsante freccia. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> il metodo per compilare questo elenco. Se il metodo indica che il progetto supporta la modifica della piattaforma, le selezioni Nuovo o Modifica vengono visualizzate anche <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> sotto l'intestazione Piattaforma. Ognuna di queste selezioni avvia finestre di dialogo che chiamano `IVsCfgProvider2` metodi per modificare le piattaforme disponibili del progetto.

   Se un progetto non supporta le piattaforme, la colonna della piattaforma per tale progetto visualizza Nessuno ed è disabilitata.

- Compilazione

   Specifica se il progetto viene compilato o meno dalla configurazione della soluzione corrente. I progetti non selezionati non vengono compilati quando i comandi di compilazione a livello di soluzione vengono richiamati nonostante le dipendenze del progetto che contengono. I progetti non selezionati per la compilazione sono ancora inclusi nel debug, nell'esecuzione, nella creazione di pacchetti e nella distribuzione della soluzione.

- Distribuisci

   Specifica se il progetto verrà distribuito quando vengono usati i comandi Avvia o Distribuisci con la configurazione di compilazione della soluzione selezionata. La casella di controllo per questo campo sarà disponibile se il progetto supporta la distribuzione implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> l'interfaccia sul relativo oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> .

  Dopo aver aggiunto una nuova configurazione della soluzione, l'utente può selezionarla dalla casella di riepilogo a discesa Configurazione soluzione sulla barra degli strumenti standard per compilare e/o avviare tale configurazione.

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
