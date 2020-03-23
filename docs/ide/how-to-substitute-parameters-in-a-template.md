---
title: Aggiungere parametri dei nomi ai modelli di progetto e di elemento
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591411"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: Sostituire i parametri di un modello

I parametri dei modelli consentono di sostituire identificatori come nomi delle classi e spazi dei nomi quando viene creato un file da un modello. È possibile aggiungere i parametri dei modelli a modelli esistenti o creare modelli personalizzati con i parametri di modello.

I parametri dei modelli vengono scritti nel formato $*parametro*$. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

Nella sezione seguente viene illustrato come modificare un modello in modo da sostituire il nome di uno spazio dei nomi con il "nome di progetto sicuro".

## <a name="example---namespace-name"></a>Esempio - nome dello spazio dei nomi

1. Inserire il parametro in uno o più dei file di codice nel modello. Ad esempio:

    ```csharp
    namespace $safeprojectname$
    ```

1. Nel file *vstemplate* per il `ProjectItem` modello, individuare l'elemento che include questo file.

1. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vedere anche

- [Creare modelli di progetto e di elemento](../ide/creating-project-and-item-templates.md)
- [Parametri del modello](../ide/template-parameters.md)
- [Informazioni di riferimento sullo schema del modello di Visual StudioVisual Studio template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
