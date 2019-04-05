---
title: Visualizzazione di file tramite l'apertura con comando | Microsoft Docs
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
ms.openlocfilehash: 0f8e5e368199a3c554499a0ca01cbb66e51fab84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970021"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Visualizzazione di file tramite il comando Apri con
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un progetto può chiedere l'IDE per visualizzare il **aperta con** nella finestra di dialogo. Questa richiesta chiede all'utente di aprire un file con una selezione dell'editor standard. I passaggi seguenti descrivono questo processo.  
  
1.  Le chiamate di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, specificando il valore OSE_UseOpenWithDialog per il `OSEOpenDocEditor` parametro.  
  
2.  Basato sull'estensione del nome file del documento, l'IDE determina quale editor elencate, è possibile del Registro di sistema aprire il documento specificato e visualizza queste informazioni nel **Apri con** nella finestra di dialogo.  
  
    > [!NOTE]
    >  Progetti con un editor intrinseco che deve essere incluso nel **aperta con** nella finestra di dialogo deve registrare una factory dell'editor per ogni tali editor. Editor intrinseco funzionare solo insieme a un particolare tipo di progetto, che viene applicato nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo). L'IDE include una factory dell'editor predefinita per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione di file Windows registrati. Un esempio di file di questo tipo è Microsoft Word.  
  
3.  Non appena l'utente seleziona un elemento dal **Apri con** finestra di dialogo, quindi l'IDE si apre il documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> (metodo). Per altre informazioni, vedere [Procedura: Aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Visualizzazione di file usando il comando Apri File](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Procedura: Aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)
