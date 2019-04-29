---
title: IDebugAlias::GetName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5858c5b559720486c24bf3fbc7562a13b9fb8372
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923870"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome dell'alias.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrName`  
 [out] Nome dell'alias.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
