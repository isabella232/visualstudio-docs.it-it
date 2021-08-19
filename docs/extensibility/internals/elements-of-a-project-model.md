---
title: Elementi di un Project modello | Microsoft Docs
description: Informazioni sugli elementi di un modello di progetto e su come le interfacce e le implementazioni di tutti i progetti in Visual Studio condividono una struttura di base.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a3e967466bef5feabaa4e6760dfc73c2927e7b35
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110579"
---
# <a name="elements-of-a-project-model"></a>Elementi di un modello di progetto
Le interfacce e le implementazioni di tutti i progetti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] condividono una struttura di base: il modello di progetto per il tipo di progetto. Nel modello di progetto, ovvero il PACCHETTO VSPackage che si sta sviluppando, si creano oggetti conformi alle decisioni di progettazione e si lavora insieme alle funzionalità globali fornite dall'IDE. Anche se si controlla la modalità di salvataggio permanente di un elemento di progetto, ad esempio, non si controlla la notifica che un file deve essere reso persistente. Quando un utente posiziona lo stato attivo  su un elemento di progetto aperto e sceglie Salva dal menu **File** sulla barra dei menu, il codice del tipo di progetto deve intercettare il comando dall'IDE, rendere persistente il file e inviare una notifica all'IDE che il file non viene più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modificato.

 Il vspackage interagisce con l'IDE tramite servizi che forniscono l'accesso alle interfacce IDE. Ad esempio, tramite determinati servizi è possibile monitorare e instradare i comandi e fornire informazioni di contesto per le selezioni effettuate nel progetto. Tutte le funzionalità ide globali necessarie per il pacchetto VSPackage vengono fornite dai servizi. Per altre informazioni sui servizi, [vedere Procedura: Ottenere un servizio.](../../extensibility/how-to-get-a-service.md)

 Altre considerazioni sull'implementazione:

- Un singolo modello di progetto può contenere più di un tipo di progetto.

- Project tipi di progetto e le factory di progetto più comuni vengono registrati in modo indipendente con GUID.

- Ogni progetto deve avere un file modello o una procedura guidata per inizializzare il nuovo file di progetto quando un utente crea un nuovo progetto tramite l'interfaccia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente. Ad esempio, i modelli inizializzano i file con estensione [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vcproj.

  La figura seguente mostra le interfacce, i servizi e gli oggetti principali che costituiscono un'implementazione tipica del progetto. È possibile usare l'helper applicazione, `HierUtil7` , per creare gli oggetti sottostanti e altri boilerplate di programmazione. Per altre informazioni sull'helper applicazione, vedere Usare le classi di progetto HierUtil7 per implementare un tipo di progetto `HierUtil7` [(C++).](/previous-versions/bb166212(v=vs.100))

  ![Visual Studio grafico del modello di](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") progetto Project modello

  Per altre informazioni sulle interfacce e sui servizi elencati nel diagramma precedente e altre interfacce facoltative non incluse nel diagramma, vedere Project [componenti di base del modello.](../../extensibility/internals/project-model-core-components.md)

  I progetti possono supportare i comandi e pertanto devono implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia per partecipare al routing dei comandi tramite i GUID del contesto di comando.

## <a name="see-also"></a>Vedi anche
- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Usare le classi di progetto HierUtil7 per implementare un tipo di progetto (C++)](/previous-versions/bb166212(v=vs.100))
- [Project componenti di base del modello](../../extensibility/internals/project-model-core-components.md)
- [Creare istanze del progetto usando le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Procedura: Ottenere un servizio](../../extensibility/how-to-get-a-service.md)
- [Creare tipi di progetto](../../extensibility/internals/creating-project-types.md)