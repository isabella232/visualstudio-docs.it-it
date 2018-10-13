---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770516b3d40097ed97a472e005c1326000291654
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260042"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il numero del tipo di argomenti di parametro per questa istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcArgs`  
 [in, out] Numero di argomenti di parametro di tipo per questa istanza.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ad esempio, se elenco\<int >, questo metodo restituisce 1 e, se elenco\<int, float2 > questo metodo restituisce 2. Questo metodo restituisce 0 se non sono presenti argomenti tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)

