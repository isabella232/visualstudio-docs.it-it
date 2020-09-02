---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99fc1e635691fa290d0a8e4506ef55d677e9ff78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547650"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene una rappresentazione dipendente dal computer dell'intervallo di indirizzi fisici associato a un stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `paddrMin`  
 out Restituisce l'indirizzo fisico più basso associato a questo stack frame.  
  
 `paddrMax`  
 out Restituisce l'indirizzo fisico più elevato associato a questo stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni restituite da questo metodo vengono utilizzate da gestione debug sessione (SDM) per ordinare gli stack frame.  
  
 Si presuppone che lo stack di chiamate diventi inattivo, ovvero che i nuovi stack frame vengano aggiunti a indirizzi di memoria sempre più bassi. Un'architettura di runtime deve fornire intervalli di stack fisici corrispondenti A questo presupposto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
