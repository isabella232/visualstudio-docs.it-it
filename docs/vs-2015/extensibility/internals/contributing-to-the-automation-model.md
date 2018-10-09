---
title: Aggiunta come contributo al modello di automazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 510faa67dc9b967e488931b149e2497bdf853d79
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526078"
---
# <a name="contributing-to-the-automation-model"></a>Aggiunta di elementi al modello di automazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta come contributo al modello di automazione](https://docs.microsoft.com/visualstudio/extensibility/internals/contributing-to-the-automation-model).  
  
Visual Studio offre un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti di creare componenti aggiuntivi di Visual Studio ed estensioni.  
  
 Inoltre, è appropriata, gli sviluppatori VSPackage di contribuire al modello di automazione. In questo modo, consentire agli utenti finali di un VSPackage per creare componenti aggiuntivi e in genere forniscono un'esperienza di modello utente coerente quando usano il pacchetto VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Per semplificare l'utente finale esperienza coerente, è possibile seguire una serie di linee guida quando si progetta il pacchetto VSPackage in modo che il modello di automazione per il pacchetto VSPackage segue le idee in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)  
 Definisce il modello di automazione come un gruppi di oggetti che consentono di controllare aspetti principali dell'ambiente comune correlati. Questo set di oggetti è raffigurato un diagramma del modello di automazione.  
  
 [Automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Descrive i due modi principali per fornire l'automazione per il pacchetto VSPackage.  
  
 [Esposizione di oggetti di progetto](../../extensibility/internals/exposing-project-objects.md)  
 Vengono fornite istruzioni dettagliate per la creazione di oggetti specifici di un pacchetto VSPackage.  
  
 [Definizione di modelli di progetto](../../extensibility/internals/project-modeling.md)  
 Vengono illustrati gli oggetti di progetto standard necessari per creare un'automazione per il nuovo tipo di progetto e viene illustrato il percorso di automazione dei progetti di seguito. In questo argomento vengono anche forniti elenchi di dichiarazioni e implementazioni per le classi.  
  
 [Esposizione di eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.  
  
 [Supporto dell'automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)  
 Viene descritto come restituire un oggetto di automazione per supportare proprietà di un pacchetto VSPackage personalizzati **opzioni** nella finestra di dialogo il **strumento** menu estendendo il `DTE.Properties` oggetto.  
  
 [Automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)  
 Viene illustrato che la creazione di un modello di automazione per il codice non è obbligatorio. Tuttavia, in questo argomento che fornisce informazioni accurate nei modelli di codice viene fornito un collegamento.  
  
 [Procedura: Fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Viene illustrato che l'automazione è una buona idea ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronte all'uso. Viene illustrata l'automazione per le finestre dei documenti e finestre degli strumenti.  
  
 [Uso del modello di automazione](../../extensibility/internals/using-the-automation-model.md)  
 Vengono forniti due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto iniziale gli oggetti di automazione.  
  
 [Automazione per la configurazione e per gli oggetti SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fornisce informazioni su automazione per le opzioni di configurazione e l'automazione per elementi selezionati.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornisce un esempio di codice che illustra come fa parte di un pacchetto VSPackage nel modello a oggetti di automazione DTE. Elenca i parametri, valori restituiti e selezionato la sezione Osservazioni.  
  
## <a name="related-sections"></a>Sezioni correlate
