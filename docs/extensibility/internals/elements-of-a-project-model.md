---
title: Elementi di un modello di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee628d56094026b588c76451c143158000636a5c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962610"
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
Le interfacce e implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto. Nel modello di progetto che è il pacchetto VSPackage si sta sviluppando, è creare oggetti conformi alle decisioni di progettazione e funziona con la funzionalità globale fornita dall'IDE. Anche se si controllano come viene mantenuto un elemento del progetto, ad esempio, non si controlla la notifica che un file deve essere persistente. Quando un utente inserisce lo stato attivo su un elemento di progetto aperto e sceglie **salvare** nel **File** menu nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu barra, il codice del tipo di progetto devono intercettare il comando dall'IDE, il file della e Invia notifica all'IDE che non sono più viene modificato il file.  
  
 Il pacchetto VSPackage interagisce con l'IDE tramite i servizi che forniscono l'accesso alle interfacce di IDE. Ad esempio, tramite il servizio specifico, di monitoraggio e la route comandi e si forniscono informazioni sul contesto per le selezioni effettuate nel progetto. Tutte le funzionalità IDE globale necessari per il pacchetto VSPackage sono fornita da servizi. Per altre informazioni sui servizi, vedere [come: Ottenere un servizio](../../extensibility/how-to-get-a-service.md).  
  
 Altre considerazioni sull'implementazione:  
  
- Un modello di progetto singolo può contenere più di un tipo di progetto.  
  
- Tipi di progetto e la factory di progetto associati vengono registrate in modo indipendente con GUID.  
  
- Ogni progetto deve avere un file di modello o una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'interfaccia utente. Ad esempio, il [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelli inizializzare cosa creò vcproj (file).  
  
  La figura seguente mostra le interfacce primarie, servizi e gli oggetti che compongono l'implementazione di un progetto tipico. È possibile usare l'helper dell'applicazione, `HierUtil7`, per creare gli oggetti sottostanti e altri standard di programmazione. Per altre informazioni sul `HierUtil7` helper dell'applicazione, vedere [HierUtil7 Usa le classi di progetto per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Rappresentazione grafica del modello di progetto Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  modello di progetto  
  
  Per altre informazioni sulle interfacce e i servizi elencati nel diagramma precedente e altre interfacce facoltative non incluse nel diagramma, vedere [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
  I progetti possono supportare i comandi e pertanto deve implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per partecipare al routing dei comandi mediante il contesto del comando GUID.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Utilizzare HierUtil7 progetto classi per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creare istanze del progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Procedura: Ottenere un servizio](../../extensibility/how-to-get-a-service.md)   
 [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)
