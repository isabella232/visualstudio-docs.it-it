---
title: "Procedura dettagliata: accesso all'oggetto DTE da un'estensione dell'editor | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148881"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Procedura dettagliata: accesso all'oggetto DTE da un'estensione dell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nei pacchetti VSPackage è possibile ottenere l'oggetto DTE chiamando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo con il tipo dell'oggetto DTE. Nelle estensioni Managed Extensibility Framework (MEF) è possibile importare <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo con un tipo di <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Recupero dell'oggetto DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Per ottenere l'oggetto DTE da ServiceProvider  
  
1. Creare un progetto VSIX C# denominato `DTETest` . Aggiungere un modello di elemento di classificazione editor e denominarlo `DTETest` . Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Aggiungere al progetto i riferimenti ad assembly seguenti:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. Immutable. 10.0  
  
3. Passare al file DTETest.cs e aggiungere le `using` direttive seguenti:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. Nella `GetDTEProvider` classe importare un oggetto <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. Nel metodo `GetClassifier()` aggiungere il codice seguente.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Se è necessario utilizzare l' <xref:EnvDTE80.DTE2> interfaccia, è possibile eseguire il cast dell'oggetto DTE.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
