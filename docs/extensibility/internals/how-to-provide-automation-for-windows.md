---
title: "Procedura: fornire l'automazione per Windows . Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707958"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per WindowsHow to: Provide automation for windows

È possibile fornire l'automazione per le finestre di documenti e strumenti. Fornire l'automazione è consigliabile ogni volta che si desidera rendere gli oggetti di automazione disponibili in una finestra e l'ambiente non fornisce già un oggetto di automazione già pronto, come accade con un elenco di attività.

## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti

L'ambiente fornisce l'automazione in <xref:EnvDTE.Window> una finestra degli strumenti restituendo un oggetto standard come illustrato nella procedura seguente:The environment provides automation on a tool window by returning a standard object as explained in the following procedure:

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> il metodo tramite l'ambiente con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` come parametro `Window` per ottenere l'oggetto.

2. Quando un chiamante richiede un oggetto di automazione specifico di `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per , , o le `IDispatch` interfacce . Entrambi `IExtensibleObject` `IVsExtensibleObject` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> forniscono un metodo.

3. Quando l'ambiente `GetAutomationObject` chiama `NULL`quindi il passaggio del metodo , rispondere passando nuovamente l'oggetto specifico di VSPackage.

4. Se `QueryInterface` la `IExtensibleObject` `IVsExtensibleObject` chiamata e l'esito negativo, l'ambiente richiede `QueryInterface` . `IDispatch`

## <a name="automation-for-document-windows"></a>Automazione per le finestre di documento

Un <xref:EnvDTE.Document> oggetto standard è disponibile anche dall'ambiente, anche se <xref:EnvDTE.Document> un `IExtensibleObject` editor può `GetAutomationObject`avere la propria implementazione dell'oggetto implementando l'interfaccia e rispondendo a .

Inoltre, un editor può fornire un oggetto di automazione specifico di VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando le `IVsExtensibleObject` interfacce o `IExtensibleObject` . Gli [esempi VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuiscono con un oggetto di automazione specifico del documento RTF.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
