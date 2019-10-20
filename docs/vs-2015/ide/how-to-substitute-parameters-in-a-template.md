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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670654"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: sostituire i parametri di un modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile sostituire i parametri di modello, ad esempio gli spazi dei nomi e i nomi delle classi, quando viene creato un file basato su un modello. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

## <a name="procedure"></a>Routine
 È possibile sostituire i parametri nei file di un modello ogni volta che viene creato un progetto basato su tale modello. Questa procedura illustra come creare un modello che sostituisce il nome di uno spazio dei nomi con il nome di progetto sicuro quando viene creato un nuovo progetto con il modello.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Per usare un parametro per sostituire il nome dello spazio dei nomi con il nome del progetto

1. Inserire il parametro in uno o più dei file di codice nel modello. Esempio:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > I parametri dei modelli vengono scritti nel formato $*parametro*$.

2. Nel file con estensione vstemplate del modello individuare l'elemento `ProjectItem` che include il file.

3. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`. Esempio:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vedere anche
 [Creazione di modelli di progetto e modelli di elemento](../ide/creating-project-and-item-templates.md) [parametri modello](../ide/template-parameters.md) di [Visual Studio riferimenti allo schema](../extensibility/visual-studio-template-schema-reference.md) dei modelli [elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
