---
title: Elementi di un modello di progetto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708533"
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
Le interfacce e le implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base, ovvero il modello di progetto per il tipo di progetto. Nel modello di progetto, ovvero il pacchetto VSPackage che si sta sviluppando, è possibile creare oggetti conformi alle decisioni di progettazione e collaborare con le funzionalità globali fornite dall'IDE. Sebbene sia possibile controllare il modo in cui un elemento del progetto viene reso permanente, ad esempio, non si controlla la notifica che un file deve essere reso permanente. Quando un utente posiziona lo stato attivo su un elemento di progetto aperto e sceglie **Salva** dal menu **file** nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra dei menu, il codice del tipo di progetto deve intercettare il comando dall'IDE, salvare in modo permanente il file e inviare la notifica all'IDE che il file non è più modificato.

 Il pacchetto VSPackage interagisce con l'IDE tramite servizi che forniscono accesso alle interfacce IDE. Ad esempio, tramite particolari servizi, è possibile monitorare e instradare i comandi e fornire informazioni di contesto per le selezioni effettuate nel progetto. Tutte le funzionalità dell'IDE globale necessarie per il pacchetto VSPackage sono fornite dai servizi. Per ulteriori informazioni sui servizi, vedere [procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md).

 Altre considerazioni sull'implementazione:

- Un modello di progetto singolo può contenere più di un tipo di progetto.

- I tipi di progetto e le factory del progetto supervisore sono registrati in modo indipendente con i GUID.

- Ogni progetto deve disporre di un file modello o di una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaccia utente. Ad esempio, i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelli inizializzano i file con estensione vcproj.

  Nella figura seguente sono illustrate le interfacce, i servizi e gli oggetti primari che compongono una tipica implementazione del progetto. È possibile usare l'helper dell'applicazione, `HierUtil7` , per creare gli oggetti sottostanti e altri standard di programmazione. Per altre informazioni sull' `HierUtil7` helper dell'applicazione, vedere [usare le classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Rappresentazione grafica del modello di progetto di Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modello di progetto

  Per ulteriori informazioni sulle interfacce e i servizi elencati nel diagramma precedente e altre interfacce facoltative non incluse nel diagramma, vedere componenti di [base del modello di progetto](../../extensibility/internals/project-model-core-components.md).

  I progetti possono supportare i comandi e pertanto devono implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per partecipare al routing dei comandi tramite i GUID del contesto del comando.

## <a name="see-also"></a>Vedere anche
- [Elenco di controllo: creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Usare le classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)
- [Creare istanze di progetto tramite Project Factory](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Procedura: ottenere un servizio](../../extensibility/how-to-get-a-service.md)
- [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
