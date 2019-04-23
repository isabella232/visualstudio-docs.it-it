---
title: "Procedura dettagliata: L'accesso all'oggetto DTE da un'estensione dell'Editor | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1319e539c185a231637b4e78d7ac0de9154ed8a3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105175"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: L'accesso all'oggetto DTE da un'estensione dell'editor
Nei pacchetti VSPackage, è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo con il tipo di oggetto DTE. Nelle estensioni di Managed Extensibility Framework (MEF), è possibile importare <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo con un tipo di <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="getting-the-dte-object"></a>Ottenere l'oggetto DTE

### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Per ottenere l'oggetto DTE da ServiceProvider

1. Creare un progetto c# VSIX denominato `DTETest`. Aggiungere un modello di elemento di classificatore Editor e denominarlo `DTETest`. Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

2. Aggiungere i riferimenti assembly seguenti al progetto:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Andare alla *DTETest.cs* del file e aggiungere il codice seguente `using` direttive:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio.Shell;

    ```

4. Nel `GetDTEProvider` classe, importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;

    ```

5. Nel metodo `GetClassifier()` aggiungere il codice seguente.

    ```csharp
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));

    ```

6. Se è necessario utilizzare il <xref:EnvDTE80.DTE2> interfaccia, è possibile eseguire il cast ad esso l'oggetto DTE.

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)