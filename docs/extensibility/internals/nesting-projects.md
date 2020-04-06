---
title: Nidificazione di progetti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707037"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VS possono raggruppare in modo pratico tipi di progetti simili utilizzando la *nidificazione dei progetti*. Ad esempio, il progetto Modello organizzazione utilizza progetti nidificati per raggruppare i progetti in categorie. I progetti di facciata aziendale, i progetti web UI e così via sono raggruppati in un'unica categoria.

 In questo scenario, non esiste alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, anche se lo sviluppatore può fornire a livello di codice i limiti. Questo tipo di raggruppamento può anche essere reso ricorsivo, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere annidati sotto l'elemento figlio per diventare un sottoprogetto dell'elemento figlio, che è un sottoprogetto dell'elemento padre.

 La nidificazione dei progetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]non è una parte intrinseca di . È necessario scrivere il codice per abilitare la nidificazione e l'annidamento di sottoprogetti all'interno di progetti figlio. Il progetto padre è un VSPackage speciale, o tipo di progetto, creato e registrato con il proprio GUID che include il codice necessario per implementare la nidificazione del progetto.

 È possibile trovare un esempio su come nidificare i progetti in [Procedura: implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Esempio di progetti annidati
 ![Soluzione di progetti annidatiNested Projects Solution](../../extensibility/internals/media/vsnestedprojects.gif "VsNestedProjects") Esempio di progetti annidati

## <a name="see-also"></a>Vedere anche
- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto di procedure guidate per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrazione di modelli di progetto e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
