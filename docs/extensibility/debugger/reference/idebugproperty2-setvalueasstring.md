---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfac70dbf625dbc689c201e5710e6f66c730aac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041438"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Imposta il valore di una proprietà da una stringa specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Stringa contenente il valore da impostare.  
  
 `nRadix`  
 [in] Una radice da utilizzare nell'interpretare le informazioni numeriche. Ciò può essere 0 per tentare di determinare automaticamente la radice.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Nella tabella seguente mostra altri valori possibili.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La stringa non può essere convertita in un valore della proprietà oppure non è stato possibile impostare il valore della proprietà.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La proprietà è in sola lettura.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)