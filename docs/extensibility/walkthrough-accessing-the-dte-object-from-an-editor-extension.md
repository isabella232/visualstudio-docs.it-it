---
title: Accedere all'oggetto DTE da un'estensione dell'editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697654"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: accedere all'oggetto DTE da un'estensione dell'editorWalkthrough: Access the DTE object from an editor extension

In VSPackage, è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo con il tipo dell'oggetto DTE. Nelle estensioni di Managed Extensibility Framework <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (MEF) <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> è possibile <xref:EnvDTE.DTE>importare e quindi chiamare il metodo con un tipo di .

## <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Ottiene l'oggetto DTE

1. Creare un progetto VSIX di C' e denominarlo **DTETest**. Aggiungere un modello di elemento **Classificatore editor** e denominarlo **DTETest**.

   Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

::: moniker range=">=vs-2019"

2. Aggiungere i seguenti riferimenti all'assembly al progetto:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Nel file *DTETestProvider.cs* aggiungere `using` le direttive seguenti:In the DTETestProvider.cs file, add the following directives:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella `DTETestProvider` classe , <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importare un file .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel `GetClassifier()` metodo aggiungere il codice `return` seguente prima dell'istruzione :

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aggiungere i seguenti riferimenti all'assembly al progetto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Nel file *DTETestProvider.cs* aggiungere `using` le direttive seguenti:In the DTETestProvider.cs file, add the following directives:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella `DTETestProvider` classe , <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>importare un file .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel `GetClassifier()` metodo aggiungere il codice `return` seguente prima dell'istruzione :

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
- [Avviare Visual Studio tramite DTE](launch-visual-studio-dte.md)
