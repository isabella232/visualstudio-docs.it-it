---
title: IDebugDisassemblyStream2::GetDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfc50f104c5fc942794c2e421f5aee508662ea3b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709330"
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
Ottiene il documento di origine associato a questo flusso di input.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDocument( 
   BSTR              bstrDocumentUrl,
   IDebugDocument2** ppDocument
);
```

```csharp
int GetDocument( 
   string              bstrDocumentUrl,
   out IDebugDocument2 ppDocument
);
```

#### <a name="parameters"></a>Parametri
 `bstrDocumentUrl`

 [in] L'URL del documento.

 `ppDocument`

 [out] Restituisce un [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) oggetto che rappresenta il documento.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene implementato da motori di debug che sono documenti di testo che non sono archiviati in un file effettivo.

## <a name="see-also"></a>Vedere anche
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)