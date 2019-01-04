---
title: Aggiunta come contributo al modello di automazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6db9cd21b56fb4d31a97fea9f16541377a8de1f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952602"
---
# <a name="contribute-to-the-automation-model"></a>Contribuire al modello di automazione
Visual Studio offre un set di interfacce di automazione per la personalizzazione dell'ambiente. Il modello di automazione è il modello a oggetti che consente agli utenti di creare componenti aggiuntivi di Visual Studio ed estensioni.  
  
 Inoltre, è appropriata, gli sviluppatori VSPackage di contribuire al modello di automazione. In questo modo, consentire agli utenti finali di un VSPackage per creare componenti aggiuntivi e in genere forniscono un'esperienza di modello utente coerente quando usano il pacchetto VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Per semplificare l'utente finale esperienza coerente, è possibile seguire una serie di linee guida quando si progetta il pacchetto VSPackage in modo che il modello di automazione per il pacchetto VSPackage segue le idee in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Cenni preliminari sul modello di automazione](../../extensibility/internals/automation-model-overview.md)  
 Definisce il modello di automazione come un gruppi di oggetti che consentono di controllare aspetti principali dell'ambiente comune correlati. Questo set di oggetti è raffigurato un diagramma del modello di automazione.  
  
 [Fornire l'automazione per i pacchetti VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Descrive i due modi principali per fornire l'automazione per il pacchetto VSPackage.  
  
 [Esporre oggetti del progetto](../../extensibility/internals/exposing-project-objects.md)  
 Vengono fornite istruzioni dettagliate per la creazione di oggetti specifici di un pacchetto VSPackage.  
  
 [Modellazione di progetto](../../extensibility/internals/project-modeling.md)  
 Vengono illustrati gli oggetti di progetto standard necessari per creare un'automazione per il nuovo tipo di progetto e viene illustrato il percorso di automazione dei progetti di seguito. In questo argomento vengono anche forniti elenchi di dichiarazioni e implementazioni per le classi.  
  
 [Esporre gli eventi](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Vengono fornite istruzioni dettagliate per la creazione di eventi per il modello di automazione.  
  
 [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)  
 Viene descritto come restituire un oggetto di automazione per supportare proprietà di un pacchetto VSPackage personalizzati **opzioni** nella finestra di dialogo il **strumento** menu estendendo il `DTE.Properties` oggetto.  
  
 [Fornire l'automazione per il codice](../../extensibility/internals/providing-automation-for-code.md)  
 Viene illustrato che la creazione di un modello di automazione per il codice non è obbligatorio. Tuttavia, in questo argomento che fornisce informazioni accurate nei modelli di codice viene fornito un collegamento.  
  
 [Procedura: Fornire l'automazione per Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Viene illustrato che l'automazione è una buona idea ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronte all'uso. Viene illustrata l'automazione per le finestre dei documenti e finestre degli strumenti.  
  
 [Usare il modello di automazione](../../extensibility/internals/using-the-automation-model.md)  
 Vengono forniti due esempi di codice che illustrano come un consumer di automazione Ottiene il progetto iniziale gli oggetti di automazione.  
  
 [Automazione per gli oggetti di configurazione e SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fornisce informazioni su automazione per gli oggetti di configurazione e SelectedItems.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornisce un esempio di codice che illustra come fa parte di un pacchetto VSPackage nel modello a oggetti di automazione DTE. Elenca i parametri, valori restituiti e selezionato la sezione Osservazioni.  
