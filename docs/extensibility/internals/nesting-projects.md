---
title: Annidamento di progetti | Microsoft Docs
description: Informazioni sull'annidamento dei progetti, che consente agli sviluppatori di applicazioni che usano il pacchetto VSPackage di raggruppare tipi simili di progetti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 86998a5af95a8c8460bfe70c09bc456bde37701d06d1a382663c0c7d83f139ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321324"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
Enterprise sviluppatori di applicazioni che usano il pacchetto VS possono raggruppare facilmente tipi simili di progetti in usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *l'annidamento del progetto*. Ad esempio, il progetto Enterprise modello usa progetti annidati per raggruppare i progetti in categorie. I progetti di facciata aziendale, i progetti di interfaccia utente Web e così via sono raggruppati in un'unica categoria.

 In questo scenario non esiste alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, anche se lo sviluppatore può fornire limiti a livello di codice. Questo tipo di raggruppamento può anche essere reso ricorsivo, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere annidati sotto l'elemento figlio per diventare un sottoprogetto dell'elemento figlio, ovvero un sottoprogetto dell'elemento padre.

 Project annidamento non è una parte intrinseca di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . È necessario scrivere il codice per abilitare l'annidamento e l'annidamento di sottoprogetti all'interno di progetti figlio. Il progetto padre è un vspackage speciale, o tipo di progetto, creato e registrato con il proprio GUID che include il codice necessario per implementare l'annidamento del progetto.

 È possibile trovare un esempio su come annidare i progetti in [Procedura: Implementare progetti annidati.](../../extensibility/internals/how-to-implement-nested-projects.md)

## <a name="nested-projects-example"></a>Esempio di progetti annidati
 ![Soluzione di progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Esempio di progetti annidati

## <a name="see-also"></a>Vedi anche
- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto di procedure guidate per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrazione di modelli di progetto e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
