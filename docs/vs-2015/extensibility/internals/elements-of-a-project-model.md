---
title: Elementi di un modello di progetto | Microsoft Docs
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
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c062ce943e2ee42cd90877827ab7b92ee33c871b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49883653"
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le interfacce e implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto. Nel modello di progetto che è il pacchetto VSPackage si sta sviluppando, è creare oggetti conformi alle decisioni di progettazione e funziona con la funzionalità globale fornita dall'IDE. Anche se si controllano come viene mantenuto un elemento del progetto, ad esempio, non si controlla la notifica che un file deve essere persistente. Quando un utente inserisce lo stato attivo su un elemento di progetto aperto e sceglie **salvare** nel **File** menu nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] menu barra, il codice del tipo di progetto devono intercettare il comando dall'IDE, il file della e Invia notifica all'IDE che non sono più viene modificato il file.  
  
 Il pacchetto VSPackage interagisce con l'IDE tramite i servizi che forniscono l'accesso alle interfacce di IDE. Ad esempio, tramite il servizio specifico, di monitoraggio e la route comandi e si forniscono informazioni sul contesto per le selezioni effettuate nel progetto. Tutte le funzionalità IDE globale necessari per il pacchetto VSPackage sono fornita da servizi. Per altre informazioni sui servizi, vedere [procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md).  
  
 Altre considerazioni sull'implementazione:  
  
- Un modello di progetto singolo può contenere più di un tipo di progetto.  
  
- Tipi di progetto e la factory di progetto associati vengono registrate in modo indipendente con GUID.  
  
- Ogni progetto deve avere un file di modello o una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dell'interfaccia utente. Ad esempio, il [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] modelli inizializzare cosa creò vcproj (file).  
  
  La figura seguente mostra le interfacce primarie, servizi e gli oggetti che compongono l'implementazione di un progetto tipico. È possibile usare l'helper dell'applicazione, HierUtil7, per creare gli oggetti sottostanti e altri standard di programmazione. Per altre informazioni sull'helper HierUtil7 dell'applicazione, vedere [non incluso nella Build: utilizzo di classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
  ![Rappresentazione grafica di Visual Studio del modello di progetto](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  modello di progetto  
  
  Per altre informazioni sulle interfacce e i servizi elencati nel diagramma precedente e altre interfacce facoltative non incluse nel diagramma, vedere [componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md).  
  
  I progetti possono supportare i comandi e pertanto deve implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per partecipare al routing dei comandi mediante il contesto del comando GUID.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Non incluso nella Build: utilizzo delle classi progetto HierUtil7 per implementare un tipo di progetto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di istanze del progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)

