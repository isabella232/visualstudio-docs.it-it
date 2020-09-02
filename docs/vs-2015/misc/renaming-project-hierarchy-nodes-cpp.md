---
title: Ridenominazione dei nodi della gerarchia del progetto (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686580"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Ridenominazione dei nodi della gerarchia del progetto (C++)
È possibile rinominare un nodo della gerarchia della cartella del progetto usando il Framework del progetto HierUtil7 per C++ non gestito. Per ulteriori informazioni, vedere l' [esempio HierUtil7](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Espansione del nodo della gerarchia  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Per espandere il nodo della gerarchia e rinominare la cartella  
  
1. Selezionare il nodo della gerarchia usando il metodo seguente:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` è il contenitore della gerarchia che corrisponde alla cartella ed `EXPF_SelectItem` è dall' <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> enumerazione. `GUID_MacroExplorer`È una costante GUID definita in vsshell. idl ed è un esempio di `rguidPersistenceSlot` nella firma della funzione di `ExtExpand` , definita in Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     È possibile trovare il file Hu_node. h nella cartella, \<installation root> \Program Files\VSIP 8.0 \ EnvSDK\common\hierutil7:  
  
2. Rinominare la cartella pubblicando il comando Rename usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` è un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> puntatore: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` Identificatore univoco del gruppo di comandi a cui appartiene il comando `cmdidRename` , definito in vsshlids. h.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di tipi di progetto](../extensibility/internals/creating-project-types.md)   
 [Esempi di VSSDK](../misc/vssdk-samples.md)