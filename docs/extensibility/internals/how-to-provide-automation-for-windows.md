---
title: 'Procedura: Fornire automazione per Windows | Microsoft Docs'
description: Informazioni su come fornire automazione per le finestre dei documenti e degli strumenti Visual Studio usando i metodi Microsoft.VisualStudio.Shell.Interop.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8d84e58bb91d49382fe4713c9ecdb6ca081d13141ef3cc2080781ca2e6b666f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388643"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: Fornire automazione per le finestre

È possibile fornire automazione per le finestre dei documenti e degli strumenti. L'automazione è consigliabile ogni volta che si vogliono rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronto, come nel caso di un elenco attività.

## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti

L'ambiente fornisce l'automazione in una finestra degli strumenti tramite la restituzione di un oggetto <xref:EnvDTE.Window> standard, come illustrato nella procedura seguente:

1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente [con __VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) come `VSFPROPID` parametro per ottenere l'oggetto `Window` .

2. Quando un chiamante richiede un oggetto di automazione specifico di VSPackage per la finestra degli strumenti tramite , l'ambiente chiama <xref:EnvDTE.Window.Object%2A> per , o le interfacce `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> `IDispatch` . Sia `IExtensibleObject` che forniscono un metodo `IVsExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> .

3. Quando l'ambiente chiama quindi il `GetAutomationObject` metodo passando , rispondere passando di nuovo `NULL` l'oggetto specifico del pacchetto VSPackage.

4. Se la chiamata `QueryInterface` a e ha esito `IExtensibleObject` `IVsExtensibleObject` negativo, l'ambiente chiama `QueryInterface` per `IDispatch` .

## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti

Un oggetto standard è disponibile anche dall'ambiente , anche se un editor può avere la propria implementazione dell'oggetto implementando l'interfaccia <xref:EnvDTE.Document> <xref:EnvDTE.Document> e `IExtensibleObject` rispondendo a `GetAutomationObject` .

Inoltre, un editor può fornire un oggetto di automazione specifico di VSPackage, recuperato tramite il metodo <xref:EnvDTE.Document.Object%2A> , implementando le `IVsExtensibleObject` interfacce o `IExtensibleObject` . Gli [esempi di VSSDK contribuiscono](https://github.com/Microsoft/VSSDK-Extensibility-Samples) a un oggetto di automazione specifico del documento RTF.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
