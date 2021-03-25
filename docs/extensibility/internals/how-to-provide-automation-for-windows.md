---
title: "Procedura: fornire l'automazione per Windows | Microsoft Docs"
description: Informazioni su come fornire l'automazione per le finestre dei documenti e degli strumenti in Visual Studio usando i metodi Microsoft. VisualStudio. Shell. Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 774b32dc1554fb6d6466be7e915fbaeea8185798
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078747"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per Windows

È possibile fornire l'automazione per le finestre dei documenti e degli strumenti. Fornire automazione è consigliabile quando si desidera rendere disponibili oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronto, come avviene con un elenco attività.

## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti

L'ambiente fornisce l'automazione in una finestra degli strumenti restituendo un <xref:EnvDTE.Window> oggetto standard come illustrato nella procedura seguente:

1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) come `VSFPROPID` parametro per ottenere l' `Window` oggetto.

2. Quando un chiamante richiede un oggetto di automazione specifico di VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A> , l'ambiente chiama `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> le interfacce, o `IDispatch` . Sia `IExtensibleObject` che `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodo.

3. Quando l'ambiente chiama il `GetAutomationObject` metodo passando `NULL` , rispondere passando l'oggetto specifico del pacchetto VSPackage.

4. Se `QueryInterface` la chiamata a per `IExtensibleObject` e ha `IVsExtensibleObject` esito negativo, l'ambiente chiama `QueryInterface` `IDispatch` .

## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti

Un <xref:EnvDTE.Document> oggetto standard è anche disponibile dall'ambiente, anche se un editor può avere la propria implementazione dell' <xref:EnvDTE.Document> oggetto implementando l' `IExtensibleObject` interfaccia e rispondendo a `GetAutomationObject` .

Inoltre, un editor può fornire un oggetto di automazione specifico di VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando le `IVsExtensibleObject` `IExtensibleObject` interfacce o. Gli [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuiscono a un oggetto di automazione RTF specifico del documento.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
