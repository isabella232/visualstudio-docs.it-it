---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f61661759f916d6d9ac82a1c17aaff11fb8242a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284804"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un'istanza di un motore di debug nel server.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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

