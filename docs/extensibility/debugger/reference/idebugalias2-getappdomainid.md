---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07c04aff053b8ce304290fefa7f56f08b448f244
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836635"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera l'identificatore per il dominio applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pappDomainId`  
 [out] Restituisce l'identificatore del dominio applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Viene creato un nuovo dominio applicazione e le modifiche di identificatore di dominio dell'applicazione ogni volta che l'applicazione viene riavviata.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)