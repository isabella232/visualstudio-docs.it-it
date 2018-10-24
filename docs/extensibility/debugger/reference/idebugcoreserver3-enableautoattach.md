---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5fc3ab0767a7077860c82acefc9554ba1228cee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831120"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Consente l'associazione automatica per i motori di debug specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rgguidSpecificEngines`  
 [in] Matrice di GUID per ogni motore di debug per contrassegnare come collegamento automatico.  
  
 `celtSpecificEngines`  
 [in] Il numero di motori specificato in `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] URL iniziale da usare quando ci si collega automaticamente.  
  
 `pbstrSessionID`  
 [out] ID della sessione che è stata collegata automaticamente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Un codice di errore `E_AUTO_ATTACH_NOT_REGISTERED`, che indica che la class factory auto-attach non è stata registrata.  
  
## <a name="remarks"></a>Note  
 Quando viene avviato un programma associato all'URL specificato, i motori di debug specificato vengono automaticamente avviati e collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)