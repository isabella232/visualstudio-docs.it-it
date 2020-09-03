---
title: Annidamento di progetti | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180426"
---
# <a name="nesting-projects"></a>Annidamento dei progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gli sviluppatori di applicazioni aziendali che utilizzano il pacchetto VS possono raggruppare in modo pratico tipi simili di progetti in utilizzando l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] *annidamento del progetto*. Il progetto modello Enterprise, ad esempio, USA i progetti annidati per raggruppare i progetti in categorie. I progetti di facciata aziendale, i progetti dell'interfaccia utente Web e così via sono raggruppati in un'unica categoria.  
  
 In questo scenario non esiste alcun limite al numero di progetti che lo sviluppatore può annidare in ogni progetto padre, sebbene lo sviluppatore possa fornire i limiti a livello di codice. Questo tipo di raggruppamento può anche essere reso ricorsivo, nel qual caso i progetti dello stesso tipo di un progetto figlio possono essere annidati sotto l'elemento figlio per diventare un sottoprogetto del figlio, che è un sottoprogetto dell'elemento padre.  
  
 L'annidamento del progetto non è una parte intrinseca di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . È necessario scrivere il codice per abilitare l'annidamento e la nidificazione del sottoprogetto nei progetti figlio. Il progetto padre è un VSPackage speciale o un tipo di progetto, creato e registrato con il proprio GUID che include il codice necessario per implementare l'annidamento del progetto.  
  
 È possibile trovare un esempio di progetti annidati nell'esempio C#. Nested Project.  
  
## <a name="nested-projects-example"></a>Esempio di progetti annidati  
 ![Soluzione di progetti annidati](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Esempio di progetti annidati  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: implementare progetti annidati](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrazione di modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementazione della gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtro della finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Elenco di controllo: creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
