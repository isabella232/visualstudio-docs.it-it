---
title: "Procedura: fornire l'automazione per Windows | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848847"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per Windows

È possibile fornire l'automazione per le finestre dei documenti e degli strumenti. Fornire automazione è consigliabile quando si desidera rendere disponibili oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronto, come avviene con un elenco attività.

## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti

L'ambiente fornisce l'automazione in una finestra degli strumenti restituendo un oggetto <xref:EnvDTE.Window> standard come illustrato nella procedura seguente:

1. Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> tramite l'ambiente con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` parametro per ottenere l'oggetto `Window`.

2. Quando un chiamante richiede un oggetto di automazione specifico di VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>o le interfacce di `IDispatch`. Sia `IExtensibleObject` che `IVsExtensibleObject` forniscono un metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Quando l'ambiente chiama il metodo `GetAutomationObject` passando `NULL`, rispondere passando l'oggetto specifico del pacchetto VSPackage.

4. Se la chiamata di `QueryInterface` per `IExtensibleObject` e `IVsExtensibleObject` ha esito negativo, l'ambiente chiama `QueryInterface` per `IDispatch`.

## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti

Dall'ambiente è disponibile anche un oggetto <xref:EnvDTE.Document> standard, anche se un editor può avere una propria implementazione dell'oggetto <xref:EnvDTE.Document> implementando `IExtensibleObject` interfaccia e rispondendo a `GetAutomationObject`.

Inoltre, un editor può fornire un oggetto di automazione specifico di VSPackage, recuperato tramite il metodo <xref:EnvDTE.Document.Object%2A>, implementando le interfacce `IVsExtensibleObject` o `IExtensibleObject`. Gli [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuiscono a un oggetto di automazione RTF specifico del documento.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
