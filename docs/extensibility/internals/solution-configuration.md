---
title: Configurazione della soluzione | Microsoft Docs
description: Informazioni su come implementare le configurazioni della soluzione supportate dal tipo di progetto, che indirizzano il comportamento della chiave di avvio (F5) e dei comandi di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6bf2694b26305cdaefefd61dc1119b7b019b12d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080788"
---
# <a name="solution-configuration"></a>Configurazione soluzione
Le configurazioni della soluzione archiviano le proprietà a livello di soluzione. Essi indirizzano il comportamento della chiave di **avvio** (F5) e dei comandi di **compilazione** . Per impostazione predefinita, questi comandi compilano e avviano la configurazione di debug. Entrambi i comandi vengono eseguiti nel contesto di una configurazione di soluzione. Ciò significa che l'utente può prevedere l'avvio di F5 e la compilazione di qualsiasi soluzione attiva configurata tramite le impostazioni. L'ambiente è progettato per ottimizzare le soluzioni anziché i progetti quando si tratta di creare ed eseguire.

 La barra degli strumenti standard di Visual Studio contiene un pulsante Start e un elenco a discesa Configurazione soluzione a destra del pulsante Avvia. Questo elenco consente agli utenti di scegliere la configurazione da avviare quando si preme F5, creare configurazioni di soluzione personalizzate o modificare una configurazione esistente.

> [!NOTE]
> Non sono disponibili interfacce di estendibilità per creare o modificare le configurazioni della soluzione. È necessario utilizzare `DTE.SolutionBuild`. Sono tuttavia disponibili API di estendibilità per la gestione della compilazione della soluzione. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Ecco come è possibile implementare le configurazioni della soluzione supportate dal tipo di progetto:

- Project

   Consente di visualizzare i nomi dei progetti presenti nella soluzione corrente.

- Configurazione

   Per fornire l'elenco delle configurazioni supportate dal tipo di progetto e visualizzate nelle pagine delle proprietà, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> .

   Nella colonna configurazione viene visualizzato il nome della configurazione del progetto da compilare in questa configurazione della soluzione ed è possibile elencare tutte le configurazioni del progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della configurazione, vengono visualizzate anche le selezioni nuove o modificate sotto l'intestazione di configurazione. Ognuna di queste selezioni avvia le finestre di dialogo che chiamano i metodi dell' `IVsCfgProvider2` interfaccia per modificare le configurazioni del progetto.

   Se un progetto non supporta le configurazioni, la colonna di configurazione Visualizza None ed è disabilitata.

- Piattaforma

   Visualizza la piattaforma per cui viene compilata la configurazione di progetto selezionata ed elenca tutte le piattaforme disponibili per il progetto quando si fa clic sul pulsante freccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> metodo per compilare questo elenco. Se il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> metodo indica che il progetto supporta la modifica della piattaforma, le selezioni nuove o modificate vengono visualizzate anche sotto l'intestazione della piattaforma. Ognuna di queste selezioni avvia le finestre di dialogo che chiamano `IVsCfgProvider2` i metodi per modificare le piattaforme disponibili del progetto.

   Se un progetto non supporta le piattaforme, la colonna della piattaforma per il progetto Visualizza None ed è disabilitata.

- Compilazione

   Specifica se il progetto viene compilato o meno dalla configurazione della soluzione corrente. I progetti non selezionati non vengono compilati quando vengono richiamati i comandi di compilazione a livello di soluzione nonostante le dipendenze del progetto in essi contenute. I progetti non selezionati per la compilazione sono ancora inclusi in debug, esecuzione, creazione di pacchetti e distribuzione della soluzione.

- Distribuisci

   Specifica se il progetto verrà distribuito quando si utilizzano i comandi Avvia o Distribuisci con la configurazione della build della soluzione selezionata. La casella di controllo per questo campo sarà disponibile se il progetto supporta la distribuzione implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaccia sul relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> oggetto.

  Una volta aggiunta una nuova configurazione di soluzione, l'utente può selezionarla dall'elenco a discesa Configurazione soluzione sulla barra degli strumenti standard per compilare e/o avviare tale configurazione.

## <a name="see-also"></a>Vedi anche
- [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)
- [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)
- [Oggetto di configurazione del progetto](../../extensibility/internals/project-configuration-object.md)
