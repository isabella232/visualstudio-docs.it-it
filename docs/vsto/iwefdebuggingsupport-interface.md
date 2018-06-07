---
title: Interfaccia IWefDebuggingSupport
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572673"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per semplificare il debug di App per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene l'interfaccia da Visual Studio e quindi chiama i metodi dell'interfaccia in determinati momenti durante la sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi che definisce l'interfaccia IWefDebuggingSupport.  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.|  
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).|  
  
  