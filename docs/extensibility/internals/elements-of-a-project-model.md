---
title: Elementi di un modello di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708533"
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
Le interfacce e le implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto. Nel modello di progetto, ovvero il pacchetto VSPackage che si sta sviluppando, si creano oggetti conformi alle decisioni di progettazione e lavorare con funzionalità globali fornite dall'IDE. Anche se si controlla la modalità di persistenza di un elemento di progetto, ad esempio, non si controlla la notifica che un file deve essere reso persistente. Quando un utente posiziona lo stato attivo su un elemento di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aperto e sceglie **Salva** dal menu **File** sulla barra dei menu, il codice del tipo di progetto deve intercettare il comando dall'IDE, rendere persistente il file e inviare la notifica all'IDE che il file non viene più modificato.

 Il pacchetto VSPackage interagisce con l'IDE tramite i servizi che forniscono l'accesso alle interfacce IDE. Ad esempio, tramite particolari servizi, è possibile monitorare e instradare i comandi e fornire informazioni di contesto per le selezioni effettuate nel progetto. Tutte le funzionalità IDE globali necessarie per il pacchetto VSPackage vengono fornite dai servizi. Per ulteriori informazioni sui servizi, vedere [Procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md).

 Altre considerazioni sull'implementazione:

- Un singolo modello di progetto può contenere più di un tipo di progetto.

- I tipi di progetto e le factory di progetto che lo accompagnano vengono registrati in modo indipendente con i GUID.

- Ogni progetto deve avere un file modello o una procedura guidata per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite l'interfaccia utente. Ad esempio, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i modelli inizializzano quelli che alla fine diventano file con estensione vcproj.

  Nella figura seguente vengono illustrate le interfacce principali, i servizi e gli oggetti che compongono un'implementazione tipica del progetto. È possibile utilizzare l'helper dell'applicazione, `HierUtil7`, per creare gli oggetti sottostanti e altri boilerplate di programmazione. Per ulteriori informazioni `HierUtil7` sull'helper dell'applicazione, vedere Usare le classi di [progetto HierUtil7 per implementare un tipo](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)di progetto (C ) .

  ![Rappresentazione grafica del modello di progetto di Visual StudioVisual Studio project model graphic](../../extensibility/internals/media/vsprojectmodel.gif "VsProjectModel (modello)") Modello di progetto

  Per ulteriori informazioni sulle interfacce e sui servizi elencati nel diagramma precedente e su altre interfacce facoltative non incluse nel diagramma, vedere [Componenti principali](../../extensibility/internals/project-model-core-components.md)del modello di progetto .

  I progetti possono supportare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> i comandi e pertanto devono implementare l'interfaccia per partecipare al routing dei comandi tramite i GUID del contesto di comando.

## <a name="see-also"></a>Vedere anche
- [Elenco di controllo: creare nuovi tipi di progettoChecklist: Create new project types](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Utilizzare le classi di progetto HierUtil7 per implementare un tipo di progetto (c'è)Use HierUtil7 project classes to implement a project type (C](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componenti principali del modello di progetto](../../extensibility/internals/project-model-core-components.md)
- [Creare istanze di progetto utilizzando le factory di progettoCreate project instances by using project factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Procedura: Ottenere un servizioHow to: Get a service](../../extensibility/how-to-get-a-service.md)
- [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)
