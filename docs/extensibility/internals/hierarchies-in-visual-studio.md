---
title: Gerarchie in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0774c4a7ad9686b02501bed80a060519f5a500f3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510410"
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) consente di visualizzare un progetto come un *gerarchia*. Nell'IDE di una gerarchia è una struttura ad albero dei nodi, in cui ogni nodo dispone di un set di proprietà associate. Oggetto *gerarchia del progetto* è un contenitore che contiene gli elementi del progetto, relazioni, degli elementi e delle proprietà dell'elemento associato e i comandi.  
  
 Nelle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è gestire le gerarchie di progetto usando l'interfaccia della gerarchia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia reindirizza i comandi richiamati dagli elementi del progetto nella finestra gerarchia appropriata anziché il gestore di comandi standard.  
  
## <a name="project-hierarchies"></a>Gerarchie di progetto  
 Ogni gerarchia del progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Ad esempio, un progetto di database potrà contenere stored procedure, viste di database e tabelle di database. Un progetto di linguaggio di programmazione, d'altra parte, probabilmente includerà i file di origine e file di risorse per le finestre di dialogo e bitmap. Le gerarchie possono essere annidate, che offre una maggiore flessibilità quando si crea una gerarchia del progetto.  
  
 Quando si crea un nuovo tipo di progetto, il tipo di progetto consente di controllare il set completo di elementi che possono essere modificate in esso. Tuttavia, i progetti possono contenere elementi per cui non hanno supporto per la modifica. Ad esempio, i progetti Visual C++ possono contenere i file HTML, anche se Visual C++ non fornisce un editor personalizzato per il tipo di file HTML.  
  
 Gerarchie di gestiscono la persistenza di elementi in che essi contenuti. L'implementazione della gerarchia debba controllare qualsiasi proprietà speciali che interessano la persistenza degli elementi all'interno della gerarchia. Ad esempio, se gli elementi rappresentano gli oggetti in un repository anziché i file, l'implementazione della gerarchia debba controllare la persistenza di tali oggetti. L'IDE stesso indirizza la gerarchia per salvare gli elementi in conformità con input utente, ma l'IDE non controlla le eventuali azioni necessarie per salvare tali elementi. Al contrario, il progetto è nel controllo.  
  
 Quando un utente apre un elemento in un editor, la gerarchia dei controlli di tale elemento è selezionata e diventa nella gerarchia attiva. La gerarchia selezionata determina il set di comandi disponibili per agire sull'elemento. Rilevamento dello stato attivo utente in questo modo consente alla gerarchia in modo da riflettere il contesto dell'utente corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di progetto](../../extensibility/internals/project-types.md)   
 [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Esempi di VSSDK](http://aka.ms/vs2015sdksamples)