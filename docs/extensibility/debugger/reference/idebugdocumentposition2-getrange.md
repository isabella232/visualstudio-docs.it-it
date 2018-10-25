---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 839e6be66ead2a5c76047f40de6142c669667673
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882436"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Ottiene l'intervallo per questa posizione del documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBegPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura compilata con la posizione iniziale. Impostare questo argomento con un valore null se questa informazione non è necessaria.  
  
 `pEndPosition`  
 [in, out] Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura compilata con la posizione finale. Impostare questo argomento con un valore null se questa informazione non è necessaria.  
  
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
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)