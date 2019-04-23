---
title: 'Procedura: Sostituire i parametri di un modello | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be004820967f85de41b11c38031722b87a5af375
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039414"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: Sostituire i parametri di un modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile sostituire i parametri di modello, ad esempio gli spazi dei nomi e i nomi delle classi, quando viene creato un file basato su un modello. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Routine  
 È possibile sostituire i parametri nei file di un modello ogni volta che viene creato un progetto basato su tale modello. Questa procedura illustra come creare un modello che sostituisce il nome di uno spazio dei nomi con il nome di progetto sicuro quando viene creato un nuovo progetto con il modello.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Per usare un parametro per sostituire il nome dello spazio dei nomi con il nome del progetto  
  
1. Inserire il parametro in uno o più dei file di codice nel modello. Ad esempio:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  I parametri dei modelli vengono scritti nel formato $*parametro*$.  
  
2. Nel file con estensione vstemplate del modello individuare l'elemento `ProjectItem` che include il file.  
  
3. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`. Ad esempio:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
