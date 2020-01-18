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
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269083"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: accesso all'oggetto DTE da un'estensione dell'editor

Nei pacchetti VSPackage è possibile ottenere l'oggetto DTE chiamando il metodo <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> con il tipo dell'oggetto DTE. Nelle estensioni Managed Extensibility Framework (MEF) è possibile importare <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e quindi chiamare il metodo <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> con un tipo di <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Ottiene l'oggetto DTE

1. Creare un C# progetto VSIX e denominarlo **DTETest**. Aggiungere un modello di elemento di **classificazione editor** e denominarlo **DTETest**.

   Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Aggiungere al progetto i riferimenti ad assembly seguenti:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Nel file *DTETestProvider.cs* aggiungere le direttive `using` seguenti:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella classe `DTETestProvider` importare una <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel metodo `GetClassifier()` aggiungere il codice seguente prima dell'istruzione `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Aggiungere al progetto i riferimenti ad assembly seguenti:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Nel file *DTETestProvider.cs* aggiungere le direttive `using` seguenti:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Nella classe `DTETestProvider` importare una <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. Nel metodo `GetClassifier()` aggiungere il codice seguente prima dell'istruzione `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
- [Avviare Visual Studio tramite DTE](launch-visual-studio-dte.md)
