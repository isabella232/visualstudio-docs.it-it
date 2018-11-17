---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
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
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eca754c3154267629a1d6567c3412ec44a0784f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809246"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera l'intervallo per la posizione corrente del documento.  
  
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
 [in, out] Offset per la posizione iniziale dell'intervallo. Impostare questo parametro su un valore null se questa informazione non è necessaria.  
  
 `pdwEndOffset`  
 [in, out] Offset per la posizione finale dell'intervallo. Impostare questo parametro su un valore null se questa informazione non è necessaria.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'intervallo specificato in una posizione di documento per un punto di interruzione di posizione viene utilizzato dal motore di debug (DE) per la ricerca con un'istruzione che effettivamente contribuisce codice. Si consideri il codice di esempio seguente:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Riga 5 non contribuisce alcun codice per il programma sottoposto a debug. Se il debugger che consente di impostare il punto di interruzione alla riga 5 desidera DE per eseguire la ricerca di un determinato periodo per la prima riga che ha reso disponibile codice, il debugger di specificare un intervallo che include le righe aggiuntive candidato in cui un punto di interruzione potrebbe essere correttamente posizionato. La Germania verrebbe quindi eseguita una ricerca in avanti tramite queste righe fino a quando non trovata una riga che può accettare un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

