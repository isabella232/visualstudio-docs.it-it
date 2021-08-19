---
title: Accedere all'oggetto DTE da un'estensione dell'editor
description: Informazioni su come accedere all'oggetto DTE da un'estensione dell'editor usando l'esempio di codice riportato in questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ffac31d74412e8f0d7a99e62374762e0dc9adad9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049207"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: Accedere all'oggetto DTE da un'estensione dell'editor

Nei pacchetti VSPackage è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo con il tipo dell'oggetto DTE. Nelle Managed Extensibility Framework (MEF) è possibile importare e <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> quindi chiamare il metodo con un tipo di <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="get-the-dte-object"></a>Ottiene l'oggetto DTE

1. Creare un progetto VSIX C# e denominarlo **DTETest**. Aggiungere un **modello di elemento Editor Classifier** e denominarlo **DTETest.**

   Per altre informazioni, vedere Creare [un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Aggiungere al progetto i riferimenti all'assembly seguenti:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Nel file *DTETestProvider.cs* aggiungere le `using` direttive seguenti:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella classe `DTETestProvider` importare un oggetto <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel metodo `GetClassifier()` aggiungere il codice seguente prima dell'istruzione `return` :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aggiungere al progetto i riferimenti all'assembly seguenti:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Nel file *DTETestProvider.cs* aggiungere le `using` direttive seguenti:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella classe `DTETestProvider` importare un oggetto <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel metodo `GetClassifier()` aggiungere il codice seguente prima dell'istruzione `return` :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
- [Avviare Visual Studio tramite DTE](launch-visual-studio-dte.md)
