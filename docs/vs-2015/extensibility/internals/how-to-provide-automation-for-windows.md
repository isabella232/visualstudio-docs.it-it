---
title: "Procedura: fornire l'automazione per Windows | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191838"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: Fornire l'automazione per Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile fornire l'automazione per le finestre dei documenti e degli strumenti. Fornire automazione è consigliabile quando si desidera rendere disponibili oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronto, come avviene con un elenco attività.  
  
## <a name="automation-for-tool-windows"></a>Automazione per le finestre degli strumenti  
 L'ambiente fornisce l'automazione in una finestra degli strumenti restituendo un <xref:EnvDTE.Window> oggetto standard come illustrato nella procedura seguente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Per fornire l'automazione per le finestre degli strumenti  
  
1. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> il `VSFPROPID` parametro As per ottenere l' `Window` oggetto.  
  
2. Quando un chiamante richiede un oggetto di automazione specifico di VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A> , l'ambiente chiama `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> le interfacce, o `IDispatch` . Sia `IExtensibleObject` che `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodo.  
  
3. Quando l'ambiente chiama il `GetAutomationObject` metodo passando `NULL` , rispondere passando l'oggetto specifico del pacchetto VSPackage.  
  
4. Se `QueryInterface` la chiamata a per `IExtensibleObject` e ha `IVsExtensibleObject` esito negativo, l'ambiente chiama `QueryInterface` `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automazione per le finestre dei documenti  
 Un <xref:EnvDTE.Document> oggetto standard è anche disponibile dall'ambiente, anche se un editor può avere la propria implementazione dell' `T:EnvDTE.Document` oggetto implementando l' `IExtensibleObject` interfaccia e rispondendo a `GetAutomationObject` .  
  
 Inoltre, un editor può fornire un oggetto di automazione specifico di VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando le `IVsExtensibleObject` `IExtensibleObject` interfacce o. Gli [esempi di VSSDK](../../misc/vssdk-samples.md) contribuiscono a un oggetto di automazione RTF specifico del documento.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
