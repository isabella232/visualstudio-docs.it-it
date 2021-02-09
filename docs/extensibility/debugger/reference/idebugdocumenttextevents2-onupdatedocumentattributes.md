---
title: 'IDebugDocumentTextEvents2:: onUpdateDocumentAttributes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2::OnUpdateDocumentAttributes
helpviewer_keywords:
- IDebugDocumentTextEvents2::onUpdateDocumentAttributes
ms.assetid: 31b7d151-9ce2-438e-b405-f8cc46b9f537
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e73b4c071f28abf80e9d35da05b0b49c96af265
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919969"
---
# <a name="idebugdocumenttextevents2onupdatedocumentattributes"></a>IDebugDocumentTextEvents2::onUpdateDocumentAttributes
Notifica al destinatario dell'evento che gli attributi del documento sono stati aggiornati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT onUpdateDocumentAttributes( 
   TEXT_DOC_ATTR_2 textdocattr
);
```

```csharp
int onUpdateDocumentAttributes( 
   enum_TEXT_DOC_ATTR_2 textdocattr
);
```

## <a name="parameters"></a>Parametri
`textdocattr`\
in Combinazione di flag dell'enumerazione [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) che specifica gli attributi aggiornati del documento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)
