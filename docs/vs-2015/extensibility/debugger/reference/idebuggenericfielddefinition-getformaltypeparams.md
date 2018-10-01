---
title: IDebugGenericFieldDefinition::GetFormalTypeParams | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3eb40b1b24ca70e0ce1f44490c80231827b5fe1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517865"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugGenericFieldDefinition::GetFormalTypeParams](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams).  
  
Recupera i parametri di tipo dato il numero di parametri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetFormalTypeParams(  
   ULONG32                   cParams,  
   IDebugGenericParamField** ppParams,  
   ULONG32*                  pcParams  
);  
```  
  
```csharp  
int GetFormalTypeParams(  
   uint                          cParams,  
   out IDebugGenericParamField[] ppParams,  
   ref uint                      pcParams  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cParams`  
 [in] Numero di parametri.  
  
 `ppParams`  
 [out] Matrice di parametri di tipo.  
  
 `pcParams`  
 [in, out] Numero di parametri in di `ppParams` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Restituisce i parametri di tipo nell'ordine da sinistra a destra. Ad esempio dizionario\<K, V > restituisce IDebugFormalGenericParameters {K, V}.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

