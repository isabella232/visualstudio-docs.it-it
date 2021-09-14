---
title: Gerarchie in Visual Studio | Microsoft Docs
description: Informazioni sulle gerarchie di progetto nel Visual Studio ide (Integrated Development Environment) che contengono elementi di progetto e le relative proprietà associate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3d8058091742f8e0f9ed3e51ebf0d046ee1524e5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709561"
---
# <a name="hierarchies-in-visual-studio"></a>Gerarchie in Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente di sviluppo integrato (IDE) visualizza un progetto come *gerarchia*. Nell'IDE una gerarchia è un albero di nodi, in cui a ogni nodo è associato un set di proprietà. Una *gerarchia di* progetto è un contenitore che contiene gli elementi del progetto, le relazioni degli elementi e le proprietà e i comandi associati degli elementi.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è possibile gestire le gerarchie dei progetti usando l'interfaccia della gerarchia , <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>L'interfaccia reindirizza i comandi richiamati dagli elementi del progetto alla finestra della gerarchia appropriata anziché al gestore dei comandi standard.

## <a name="project-hierarchies"></a>Project gerarchie
 Ogni gerarchia di progetto contiene elementi che è possibile visualizzare e modificare. Questi elementi variano a seconda del tipo di progetto. Ad esempio, un progetto di database può contenere stored procedure, viste di database e tabelle di database. Un progetto di linguaggio di programmazione, d'altra parte, includerà probabilmente file di origine e file di risorse per bitmap e finestre di dialogo. Le gerarchie possono essere annidate, con una maggiore flessibilità quando si crea una gerarchia di progetto.

 Quando si crea un nuovo tipo di progetto, il tipo di progetto controlla il set completo di elementi che è possibile modificare. Tuttavia, i progetti possono contenere elementi per i quali non dispongono del supporto per la modifica. Ad esempio, Visual C++ possono contenere file HTML, anche se Visual C++ non fornisce alcun editor personalizzato per il tipo di file HTML.

 Le gerarchie gestiscono la persistenza degli elementi che contengono. L'implementazione della gerarchia deve controllare le proprietà speciali che influiscono sulla persistenza degli elementi all'interno della gerarchia. Ad esempio, se gli elementi rappresentano oggetti in un repository anziché in file, l'implementazione della gerarchia deve controllare la persistenza di tali oggetti. L'IDE stesso indica alla gerarchia di salvare gli elementi in conformità con l'input dell'utente, ma l'IDE non controlla le azioni necessarie per salvare tali elementi. Al contrario, il progetto è in controllo.

 Quando un utente apre un elemento in un editor, la gerarchia che controlla tale elemento viene selezionata e diventa la gerarchia attiva. La gerarchia selezionata determina il set di comandi disponibili per agire sull'elemento. Il rilevamento dello stato attivo dell'utente in questo modo consente alla gerarchia di riflettere il contesto corrente dell'utente.

## <a name="see-also"></a>Vedi anche
- [Project tipi](../../extensibility/internals/project-types.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
