---
title: Lo stato del VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: douge
ms.openlocfilehash: 2891e3f8f9022aad3d16245ae1553a1a9fec3ec7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540698"
---
# <a name="vspackage-state"></a>Stato di un pacchetto VSPackage
Molti fattori determinano il set di valori persistenti o stato, di un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dell'applicazione.  
  
-   I progetti dispongono di proprietà di configurazione e progetto.  
  
-   Le soluzioni hanno le proprietà.  
  
-   Impostazioni utente determinano le dimensioni e posizione delle finestre dei documenti, finestre degli strumenti, stato di ancoraggio e tasti di scelta rapida.  
  
-   Le applicazioni possono contenere opzioni impostati da un utente.  
  
-   Gli oggetti che crea un'applicazione possono disporre di proprietà proprie.  
  
 Ecco alcuni dei metodi che un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lo stato dell'applicazione può essere gestito:  
  
-   Tramite le pagine di proprietà di progetto e soluzione.  
  
-   Tramite il **importazione / esportazione guidata delle impostazioni**, che consente all'utente di spostare le impostazioni da un computer a un altro.  
  
-   Tramite il **opzioni** della finestra di dialogo che include le opzioni relative alle applicazioni.  
  
-   Tramite il **proprietà** finestra, che espone le proprietà degli oggetti.  
  
-   Grazie all'automazione. Un'applicazione può accedere a VSPackage e l'oggetto proprietà che sono stati esposti all'automazione.  
  
 Lo stato dell'applicazione sottostante sono vari meccanismi di persistenza che abilitano lo stato dell'applicazione essere salvato e ripristinato.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Supporto per la persistenza dello stato](../misc/support-for-state-persistence.md)  
 Vengono elencate le strategie comuni per salvare, ripristinare e reimpostare lo stato di un VSPackage.  
  
 [Opzioni e pagine di opzioni](../extensibility/internals/options-and-options-pages.md)  
 Introduce le pagine di opzioni generali e personalizzate e viene spiegato come implementarle.  
  
 [Creazione di una pagina di opzioni](../extensibility/creating-an-options-page.md)  
 Viene illustrato come creare due pagine di opzioni, una semplice pagina e una pagina personalizzata.  
  
 [Supporto per le categorie di impostazioni](../misc/support-for-settings-categories.md)  
 Vengono illustrate le impostazioni utente e come vengono creati e salvati in modo permanente.  
  
 [Creazione di una categoria di impostazioni](../extensibility/creating-a-settings-category.md)  
 Viene illustrato come creare un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoria di impostazioni e usarlo per salvare i valori e ripristinare i valori da un file di impostazioni.  
  
 [Estensione delle proprietà e della finestra Proprietà](../extensibility/extending-properties-and-the-property-window.md)  
 Viene illustrato come visualizzare e modificare il valore di un oggetto nel **proprietà** finestra.  
  
 [Esposizione di proprietà nella finestra Proprietà](../extensibility/exposing-properties-to-the-properties-window.md)  
 Viene illustrato come esporre le proprietà pubbliche di un oggetto per il **proprietà** finestra.  
  
 [Supporto per le proprietà di configurazione e del progetto](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Viene illustrato come visualizzare e modificare le proprietà di configurazione e progetto.  
  
 [Recupero delle proprietà del progetto](../extensibility/getting-project-properties.md)  
 Modo semplificato i passaggi per la creazione di un pacchetto VSPackage gestito che consente di visualizzare le proprietà del progetto in una finestra degli strumenti.  
  
 [Uso dell'archivio delle impostazioni](../extensibility/using-the-settings-store.md)  
 Viene illustrato il meccanismo di persistenza delle impostazioni Store e come usarlo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)  
 Viene fornito un orientamento generale ad argomenti che illustrano come creare e usare i pacchetti VSPackage.