---
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee33cff1ba8ee6ce278a9bb11f8967d4dd377173
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925274"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
Utilizzata per impostare i punti di interruzione di codice basati su una stringa che l'utente può immettere dall'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>Membri  
 `bstrContext`  
 Contesto del punto di interruzione all'interno del codice, in genere un nome di metodo o una funzione come visualizzato in uno stack di chiamate.  
  
 `bstrCodeExpr`  
 Stringa che l'utente digita per descrivere il punto di interruzione del codice.  
  
## <a name="remarks"></a>Note  
 Questa struttura è un membro del [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)