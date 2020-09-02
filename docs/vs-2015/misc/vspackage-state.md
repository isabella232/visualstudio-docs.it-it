---
title: Stato VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979995"
---
# <a name="vspackage-state"></a>Stato di un pacchetto VSPackage
Molti fattori determinano il set di valori salvati in permanenza, o stato, di un' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] applicazione.  
  
- I progetti dispongono di proprietà di progetto e di configurazione.  
  
- Le soluzioni dispongono di proprietà.  
  
- Le impostazioni utente determinano le dimensioni e la posizione delle finestre del documento, delle finestre degli strumenti, dello stato di ancoraggio e dei tasti di scelta rapida.  
  
- Le applicazioni possono disporre di opzioni impostate da un utente.  
  
- Gli oggetti creati da un'applicazione possono avere proprietà personalizzate.  
  
  Di seguito sono riportati alcuni modi in cui è [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] possibile gestire uno stato dell'applicazione:  
  
- Tramite le pagine delle proprietà del progetto e della soluzione.  
  
- Tramite l' **importazione/esportazione guidata delle impostazioni**, che consente a un utente di spostare le impostazioni da un computer a un altro.  
  
- Nella finestra di dialogo **Opzioni** , che include le opzioni correlate alle applicazioni.  
  
- Tramite la finestra **Proprietà** , che espone le proprietà degli oggetti.  
  
- Tramite l'automazione. Un'applicazione può accedere alle proprietà VSPackage e Object che sono state esposte all'automazione.  
  
  Lo stato dell'applicazione sottostante è costituito da vari meccanismi di persistenza che consentono di salvare e ripristinare lo stato dell'applicazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Supporto per la persistenza dello stato](../misc/support-for-state-persistence.md)  
 Vengono elencate le strategie comuni per salvare, ripristinare e reimpostare lo stato di un VSPackage.  
  
 [Opzioni e pagine di opzioni](../extensibility/internals/options-and-options-pages.md)  
 Introduce le pagine di opzioni generali e personalizzate e spiega come implementarle.  
  
 [Creazione di una pagina di opzioni](../extensibility/creating-an-options-page.md)  
 Viene illustrato come creare due pagine di opzioni, una pagina semplice e una pagina personalizzata.  
  
 [Supporto per le categorie di impostazioni](../misc/support-for-settings-categories.md)  
 Vengono illustrate le impostazioni utente e il modo in cui vengono create e rese permanente.  
  
 [Creazione di una categoria di impostazioni](../extensibility/creating-a-settings-category.md)  
 Viene illustrato come creare una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoria di impostazioni e usarla per salvare i valori e ripristinare i valori da un file di impostazioni.  
  
 [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)  
 Viene illustrato come visualizzare e modificare il valore di un oggetto nella finestra **Proprietà** .  
  
 [Esposizione di proprietà nella finestra Proprietà](../extensibility/exposing-properties-to-the-properties-window.md)  
 Viene illustrato come esporre le proprietà pubbliche di un oggetto nella finestra **Proprietà** .  
  
 [Supporto per le proprietà di configurazione e del progetto](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Viene illustrato come visualizzare e modificare le proprietà di progetto e di configurazione.  
  
 [Recupero delle proprietà del progetto](../extensibility/getting-project-properties.md)  
 Vengono illustrati i passaggi per la creazione di un pacchetto VSPackage gestito che visualizza le proprietà del progetto in una finestra degli strumenti.  
  
 [Uso dell'archivio delle impostazioni](../extensibility/using-the-settings-store.md)  
 Viene illustrato il meccanismo di persistenza dell'archivio impostazioni e come utilizzarlo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Fornisce un orientamento generale ad argomenti che illustrano come creare e usare i pacchetti VSPackage.