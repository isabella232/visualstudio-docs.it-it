---
title: Aggiungere parametri dei nomi ai modelli di progetto e di elemento
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fa06783acf3feaa863b788c3c0b976b0c762d0c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986908"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Procedura: Sostituire i parametri di un modello

I parametri dei modelli consentono di sostituire identificatori come nomi delle classi e spazi dei nomi quando viene creato un file da un modello. È possibile aggiungere i parametri dei modelli a modelli esistenti o creare modelli personalizzati con i parametri di modello.

I parametri dei modelli vengono scritti nel formato $*parametro*$. Per un elenco completo dei parametri dei modelli, vedere [Parametri di modelli](../ide/template-parameters.md).

Nella sezione seguente viene illustrato come modificare un modello in modo da sostituire il nome di uno spazio dei nomi con il "nome di progetto sicuro".

## <a name="to-use-a-parameter-to-replace-the-namespace-name"></a>Per usare un parametro per sostituire il nome dello spazio dei nomi

1. Inserire il parametro in uno o più dei file di codice nel modello. Ad esempio:

    ```csharp
    namespace $safeprojectname$
    ```

1. Nel file *vstemplate* del modello individuare l'elemento `ProjectItem` che include il file.

1. Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Vedere anche

- [Creare modelli di progetto e di elementi](../ide/creating-project-and-item-templates.md)
- [Parametri di modello](../ide/template-parameters.md)
- [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento ProjectItem (modelli di elemento di Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)