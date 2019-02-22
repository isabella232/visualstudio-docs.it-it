---
title: Annidamento dei progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2e05b47563c62f34e4a01c945a45d5c7ec069ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612231"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
Gli sviluppatori di applicazioni aziendali che usano il pacchetto di Visual Studio possono raggruppano tipi simili di progetti nell'insieme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando *progetto annidamento*. Ad esempio, il progetto di modello dell'organizzazione Usa i progetti annidati per i progetti di gruppo in categorie. Progetti di facciata business, i progetti di interfaccia utente Web e così via vengono raggruppati insieme in una categoria.

 In questo scenario non è alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, anche se lo sviluppatore può fornire a livello di programmazione i limiti. Questo tipo di raggruppamento può inoltre essere creato ricorsiva, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere nidificati sotto l'elemento figlio per diventare un sottoprogetto del figlio, che è un sottoprogetto del padre.

 Annidamento di progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È necessario scrivere il codice per abilitare la nidificazione e un sottoprogetto annidamento all'interno dei progetti figlio. Il progetto padre è un pacchetto VSPackage speciali o tipo di progetto creato e registrato con un proprio GUID che include il codice necessario per implementare la nidificazione di progetto.

 Nell'esempio c# Example.Nested Project, è possibile trovare un esempio di progetti annidati.

## <a name="nested-projects-example"></a>Esempio di progetti annidati
 ![Esplora i progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") esempio i progetti annidati

## <a name="see-also"></a>Vedere anche
- [Procedura: Implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md)
- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto di procedure guidate per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrazione di modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Applicazione di un filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)