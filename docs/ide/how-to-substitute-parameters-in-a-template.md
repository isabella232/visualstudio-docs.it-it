---
title: Aggiungere parametri dei nomi ai modelli di progetto e di elemento
description: Informazioni su come modificare i parametri del modello per sostituire gli identificatori, ad esempio i nomi delle classi e gli spazi dei nomi.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ba830035f441421ca0eb83404b37319d9a9e2ca3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596859"
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

1. Nel file *vstemplate* del modello individuare l' `ProjectItem` elemento che include il file.

1. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vedere anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modelli](../ide/template-parameters.md)
- [Riferimento allo schema di modello di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
