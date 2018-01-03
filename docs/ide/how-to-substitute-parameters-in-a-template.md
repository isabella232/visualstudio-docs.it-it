---
title: 'Procedura: Sostituire i parametri di un modello | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 73a59dc1c0e43867ae76d1daaf5d8adf73fae4c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: sostituire i parametri di un modello
È possibile sostituire i parametri di modello, ad esempio gli spazi dei nomi e i nomi delle classi, quando viene creato un file basato su un modello. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Routine  
 È possibile sostituire i parametri nei file di un modello ogni volta che viene creato un progetto basato su tale modello. Questa procedura illustra come creare un modello che sostituisce il nome di uno spazio dei nomi con il nome di progetto sicuro quando viene creato un nuovo progetto con il modello.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Per usare un parametro per sostituire il nome dello spazio dei nomi con il nome del progetto  
  
1.  Inserire il parametro in uno o più dei file di codice nel modello. Ad esempio:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  I parametri dei modelli vengono scritti nel formato $*parametro*$.  
  
2.  Nel file con estensione vstemplate del modello individuare l'elemento `ProjectItem` che include il file.  
  
3.  Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`. Ad esempio:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)