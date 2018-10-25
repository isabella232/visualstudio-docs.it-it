---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 171eda8b7c1b206ea54839366686ad43f690afe0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886474"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea un'istanza di un motore di debug nel server.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szDll`  
 [in] Percorso della dll che implementa il CLSID specificato nella `clsidObject` parametro. Se si tratta `NULL`, quindi COM `CoCreateInstance` funzione viene chiamata.  
  
 `wLangId`  
 [in] Impostazioni locali del motore di debug. Questo può essere 0 se il [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) metodo non deve essere chiamato.  
  
 `clsidObject`  
 [in] CLSID del motore di debug da creare.  
  
 `riid`  
 [in] ID dell'interfaccia dell'interfaccia specifica per il recupero dall'oggetto classe.  
  
 `ppvObject`  
 [out] `IUnknown` interfaccia dall'oggetto di un'istanza. Eseguire il cast o effettuare il marshalling di questo oggetto all'interfaccia desiderata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)