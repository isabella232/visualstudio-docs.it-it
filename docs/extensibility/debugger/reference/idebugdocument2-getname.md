---
title: IDebugDocument2::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1c819c63a40a1d7f08b46b67a8cfd2c1949c074
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905212"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ottiene il nome del documento in uno dei diversi formati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `gnType`  
 [in] Un valore compreso il [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumerazione che determina il tipo del nome da restituire.  
  
 `pbstrFileName`  
 [out] Restituisce una stringa contenente il nome del documento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo può, ad esempio, restituire il nome del documento come un titolo o come nome del file o persino parte di un nome file.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)