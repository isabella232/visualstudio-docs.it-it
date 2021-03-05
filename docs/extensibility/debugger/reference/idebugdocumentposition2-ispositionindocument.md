---
description: Determina se la posizione del documento è contenuta nel documento specificato.
title: 'IDebugDocumentPosition2:: IsPositionInDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a4800f3735e2d015e3638a642e8c0d54829ddd4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154288"
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

## <a name="parameters"></a>Parametri
`pDoc`\
in Oggetto [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) che rappresenta il candidato del documento contenitore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene utilizzato principalmente per l'impostazione di punti di interruzione nelle interfacce [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) . Quando vengono caricati i documenti, viene chiamata la posizione del punto di interruzione per determinare se il documento contiene questa posizione.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
