---
title: Accedere all'oggetto DTE da un'estensione dell'editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fb22793c3bfa805fae11c8bbea7f07c06fd5a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322795"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: Accedere all'oggetto DTE da un'estensione dell'editor

Nei pacchetti VSPackage, è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo con il tipo di oggetto DTE. Nelle estensioni di Managed Extensibility Framework (MEF), è possibile importare <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo con un tipo di <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Ottiene l'oggetto DTE

1. Creare un C# VSIX di progetto e denominarla **DTETest**. Aggiungere un **classificatore Editor** modello di elemento e denominarlo **DTETest**.

   Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Aggiungere il riferimento all'assembly seguente al progetto:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Nel *DTETestProvider.cs* del file, aggiungere il codice seguente `using` direttive:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nel `DTETestProvider` classe, importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel `GetClassifier()` metodo, aggiungere il codice seguente prima di `return` istruzione:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aggiungere i riferimenti assembly seguenti al progetto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Nel *DTETestProvider.cs* del file, aggiungere il codice seguente `using` direttive:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nel `DTETestProvider` classe, importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel `GetClassifier()` metodo, aggiungere il codice seguente prima di `return` istruzione:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
- [Avviare Visual Studio usando DTE](launch-visual-studio-dte.md)