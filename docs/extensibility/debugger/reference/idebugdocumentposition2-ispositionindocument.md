---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5701df9085de7a63e7f09ea37c28244897122b7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678917"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Determina se la posizione del documento è contenuta nel documento specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsPositionInDocument( 
   IDebugDocument2* pDoc
);
```

```csharp
int IsPositionInDocument( 
   IDebugDocument2 pDoc
);
```

#### <a name="parameters"></a>Parametri
 `pDoc`

 [in] Il [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) oggetto che rappresenta il candidato di documento che lo contiene.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene utilizzato principalmente in impostando punti di interruzione [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfacce. Man mano che vengono caricati documenti, la posizione del punto di interruzione viene chiamata per determinare se il documento contiene questa posizione.

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)