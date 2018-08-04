---
title: "Procedura: fornire l'automazione per Windows | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9158ac7d133d30ae5fbca0281cbc55138e041f6
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510738"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per windows
È possibile fornire l'automazione per finestre degli strumenti e documenti. Automazione fornendo è consigliabile ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronte all'uso, come accade con un elenco di attività.

## <a name="automation-for-tool-windows"></a>Automazione per finestre degli strumenti
 L'ambiente fornisce l'automazione in una finestra degli strumenti, restituendo uno standard <xref:EnvDTE.Window> dell'oggetto come illustrato nella procedura seguente:

### <a name="to-provide-automation-for-tool-windows"></a>Per fornire l'automazione per finestre degli strumenti

1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> come `VSFPROPID` parametro per ottenere il `Window` oggetto.

2.  Quando un chiamante richiede un oggetto di automazione specifico del VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o `IDispatch` interfacce. Entrambe `IExtensibleObject` e `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (metodo).

3.  Quando l'ambiente chiama quindi il `GetAutomationObject` metodo passando `NULL`, rispondere passando nuovamente l'oggetto specifico del VSPackage.

4.  Se il chiamante `QueryInterface` per `IExtensibleObject` e `IVsExtensibleObject` ha esito negativo, l'ambiente chiama `QueryInterface` per `IDispatch`.

## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti
 Uno standard <xref:EnvDTE.Document> oggetto è anche disponibile dall'ambiente, sebbene un editor può avere una propria implementazione del <xref:EnvDTE.Document> oggetto implementando `IExtensibleObject` interfaccia e risponde alle `GetAutomationObject`.

 Inoltre, un editor può fornire un oggetto di automazione specifico del VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando la `IVsExtensibleObject` o `IExtensibleObject` interfacce. Il [esempi di VSSDK](http://aka.ms/vs2015sdksamples) contribuisce a un oggetto di automazione specifiche del documento RTF.

## <a name="see-also"></a>Vedere anche
    
<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>