---
title: IDebugExtendedField::GetExtendedKind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5e1be1da0ca207f5bc030bf5de72efdb0d24ea8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897602"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Recupera il tipo di campo estese specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExtendedKind(  
   FIELD_KIND_EX* pdwKind  
);  
```  
  
```csharp  
int GetExtendedKind(  
   ref enum_FIELD_KIND_EX pdwKind  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwKind`  
 [in, out] Valore di [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) enumerazione che definisce il tipo di campo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)