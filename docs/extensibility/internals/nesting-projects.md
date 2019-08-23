---
title: Annidamento di progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289062a15c35641d5558409c7643301e346b6e65
ms.sourcegitcommit: f42b5318c5c93e2b5ecff44f408fab8bcdfb193d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69976699"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto vs possono raggruppare in modo pratico tipi simili [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetti in utilizzando l'annidamento del *progetto*. Il progetto modello Enterprise, ad esempio, USA i progetti annidati per raggruppare i progetti in categorie. I progetti di facciata aziendale, i progetti dell'interfaccia utente Web e così via sono raggruppati in un'unica categoria.

 In questo scenario non esiste alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, sebbene lo sviluppatore possa fornire i limiti a livello di codice. Questo tipo di raggruppamento può anche essere reso ricorsivo, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere annidati sotto l'elemento figlio per diventare un sottoprogetto del figlio, che è un sottoprogetto dell'elemento padre.

 L'annidamento del progetto non è una parte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]intrinseca di. È necessario scrivere il codice per abilitare l'annidamento e la nidificazione del sottoprogetto nei progetti figlio. Il progetto padre è un VSPackage speciale o un tipo di progetto, creato e registrato con il proprio GUID che include il codice necessario per implementare l'annidamento del progetto.

 È possibile trovare un esempio su come annidare i [progetti in procedura: Implementare progetti](../../extensibility/internals/how-to-implement-nested-projects.md)annidati.

## <a name="nested-projects-example"></a>Esempio di progetti annidati
 ![Soluzione di progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Esempio di progetti annidati

## <a name="see-also"></a>Vedere anche
- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto di procedure guidate per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrazione di modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Elenco di controllo: creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
