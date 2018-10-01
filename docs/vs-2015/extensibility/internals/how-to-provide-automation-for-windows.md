---
title: "Procedura: fornire l'automazione per Windows | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fad49e2841186cea677a165bdb48c4a1af5b41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527979"
---
# <a name="how-to-provide-automation-for-windows"></a>Procedura: fornire l'automazione per Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: fornire l'automazione per Windows](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-automation-for-windows).  
  
È possibile fornire l'automazione per finestre degli strumenti e documenti. Automazione fornendo è consigliabile ogni volta che si desidera rendere disponibili gli oggetti di automazione in una finestra e l'ambiente non fornisce già un oggetto di automazione pronte all'uso, come accade con un elenco di attività.  
  
## <a name="automation-for-tool-windows"></a>Automazione per lo strumento Windows  
 L'ambiente fornisce l'automazione in una finestra degli strumenti, restituendo uno standard <xref:EnvDTE.Window> dell'oggetto come illustrato nella procedura seguente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Per fornire l'automazione per finestre degli strumenti  
  
1.  Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodo tramite l'ambiente con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> come `VSFPROPID` parametro per ottenere il `Window` oggetto.  
  
2.  Quando un chiamante richiede un oggetto di automazione specifico del VSPackage per la finestra degli strumenti tramite <xref:EnvDTE.Window.Object%2A>, l'ambiente chiama `QueryInterface` per `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o `IDispatch` interfacce. Entrambe `IExtensibleObject` e `IVsExtensibleObject` forniscono un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> (metodo).  
  
3.  Quando l'ambiente chiama quindi il `GetAutomationObject` metodo passando `NULL`, rispondere passando nuovamente l'oggetto specifico del VSPackage.  
  
4.  Se il chiamante `QueryInterface` per `IExtensibleObject` e `IVsExtensibleObject` ha esito negativo, l'ambiente chiama `QueryInterface` per `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automazione per Windows di documento  
 Uno standard <xref:EnvDTE.Document> oggetto è anche disponibile dall'ambiente, sebbene un editor può avere una propria implementazione del `T:EnvDTE.Document` oggetto implementando `IExtensibleObject` interfaccia e risponde alle `GetAutomationObject`.  
  
 Inoltre, un editor può fornire un oggetto di automazione specifico del VSPackage, recuperato tramite il <xref:EnvDTE.Document.Object%2A> metodo, implementando la `IVsExtensibleObject` o `IExtensibleObject` interfacce. Il [esempi di VSSDK](../../misc/vssdk-samples.md) contribuisce a un oggetto di automazione specifiche del documento RTF.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

