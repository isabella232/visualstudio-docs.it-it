---
title: Visualizzazione di file tramite il comando Apri con | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839436"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Visualizzazione di file tramite il comando Apri con
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un progetto può richiedere all'IDE di visualizzare la finestra di dialogo **Apri con** . Questa richiesta richiede all'utente di aprire un file con una selezione di editor standard. Questo processo è descritto nella seguente procedura.  
  
1. Il progetto chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , specificando il valore OSE_UseOpenWithDialog per il `OSEOpenDocEditor` parametro.  
  
2. In base all'estensione del nome di file del documento, l'IDE determina quali editor elencati nel registro di sistema possono aprire il documento specificato e visualizza queste informazioni nella finestra **di dialogo Apri con** .  
  
    > [!NOTE]
    > I progetti che dispongono di un editor intrinseco che deve essere incluso nella finestra di dialogo **Apri con** devono registrare una factory dell'editor per ogni editor di questo tipo. Gli editor intrinseci funzionano solo insieme a un determinato tipo di progetto, che viene applicato nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. L'IDE include una factory dell'editor predefinita per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione di file di Windows registrata. Un esempio di tale file è Microsoft Word.  
  
3. Non appena l'utente seleziona un elemento dalla finestra di dialogo **Apri con** , l'IDE apre il documento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo. Per altre informazioni, vedere [procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
