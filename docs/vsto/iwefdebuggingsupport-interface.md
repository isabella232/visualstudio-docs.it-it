---
title: Interfaccia IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55a09c3db9a47b5bcf22a7faeb891a1f709d244a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865684"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per facilitare il debug delle App per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene questa interfaccia da Visual Studio e quindi chiama i metodi sull'interfaccia in determinati momenti durante la sessione di debug.  
  
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
 Nella tabella seguente elenca i metodi che definisce l'interfaccia IWefDebuggingSupport.  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.|  
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che eseguirà il contenuto Web estensioni Framework (WCF).|  
