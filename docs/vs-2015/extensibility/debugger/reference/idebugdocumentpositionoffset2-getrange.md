---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200238"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera l'intervallo per la posizione del documento corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwBegOffset`  
 [in, out] Offset per la posizione iniziale dell'intervallo. Se queste informazioni non sono necessarie, impostare questo parametro su un valore null.  
  
 `pdwEndOffset`  
 [in, out] Offset per la posizione finale dell'intervallo. Se queste informazioni non sono necessarie, impostare questo parametro su un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 L'intervallo specificato in una posizione del documento per un punto di interruzione del percorso viene utilizzato dal motore di debug (DE) per eseguire una ricerca in avanti di un'istruzione che contribuisce effettivamente al codice. Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La riga 5 non contribuisce al programma di cui è in corso il debug. Se il debugger che imposta il punto di interruzione nella riga 5 vuole che il DE cerchi in avanti una determinata quantità per la prima riga che contribuisce al codice, il debugger specifica un intervallo che include righe candidati aggiuntive in cui un punto di interruzione può essere posizionato correttamente. Il DE, quindi, ricercherà le righe fino a trovare una riga che potrebbe accettare un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
