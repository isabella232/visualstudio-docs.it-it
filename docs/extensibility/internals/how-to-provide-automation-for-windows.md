---
title: "Procedura: Fornire l'automazione per Windows | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 190372e44f068296f7fea14819a3520803b89406
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843136"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: Fornire l'automazione per windows

È possibile fornire l'automazione per finestre degli strumenti e documenti. Automazione fornendo è consigliabile ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronte all'uso, come accade con un elenco di attività.

## <a name="automation-for-tool-windows"></a>Automazione per finestre degli strumenti

L'ambiente fornisce l'automazione in una finestra degli strumenti, restituendo uno standard <xref:EnvDTE.Window> dell'oggetto come illustrato nella procedura seguente:

1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) come `VSFPROPID` parametro per ottenere il `Window` oggetto.

2.  Quando un chiamante richiede un oggetto di automazione specifico del VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o `IDispatch` interfacce. Entrambe `IExtensibleObject` e `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (metodo).

3.  Quando l'ambiente chiama quindi il `GetAutomationObject` metodo passando `NULL`, rispondere passando nuovamente l'oggetto specifico del VSPackage.

4.  Se il chiamante `QueryInterface` per `IExtensibleObject` e `IVsExtensibleObject` ha esito negativo, l'ambiente chiama `QueryInterface` per `IDispatch`.

## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti

Uno standard <xref:EnvDTE.Document> oggetto è anche disponibile dall'ambiente, sebbene un editor può avere una propria implementazione del <xref:EnvDTE.Document> oggetto implementando `IExtensibleObject` interfaccia e risponde alle `GetAutomationObject`.

Inoltre, un editor può fornire un oggetto di automazione specifico del VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando la `IVsExtensibleObject` o `IExtensibleObject` interfacce. Il [esempi di VSSDK](https://aka.ms/vs2015sdksamples) contribuisce a un oggetto di automazione specifiche del documento RTF.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>