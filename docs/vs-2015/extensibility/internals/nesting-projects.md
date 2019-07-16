---
title: Annidamento dei progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180426"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli sviluppatori di applicazioni aziendali che usano il pacchetto di Visual Studio possono raggruppano tipi simili di progetti nell'insieme [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando *progetto annidamento*. Ad esempio, il progetto di modello dell'organizzazione Usa i progetti annidati per i progetti di gruppo in categorie. Progetti di facciata business, i progetti di interfaccia utente Web e così via vengono raggruppati insieme in una categoria.  
  
 In questo scenario non è alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, anche se lo sviluppatore può fornire a livello di programmazione i limiti. Questo tipo di raggruppamento può inoltre essere creato ricorsiva, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere nidificati sotto l'elemento figlio per diventare un sottoprogetto del figlio, che è un sottoprogetto del padre.  
  
 Annidamento di progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. È necessario scrivere il codice per abilitare la nidificazione e un sottoprogetto annidamento all'interno dei progetti figlio. Il progetto padre è un pacchetto VSPackage speciali o tipo di progetto creato e registrato con un proprio GUID che include il codice necessario per implementare la nidificazione di progetto.  
  
 Nell'esempio c# Example.Nested Project, è possibile trovare un esempio di progetti annidati.  
  
## <a name="nested-projects-example"></a>Esempio di progetti annidati  
 ![Esplora i progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Esempio di progetti annidati  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerazioni per lo scaricamento e ricaricare i progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Il filtro nella finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
