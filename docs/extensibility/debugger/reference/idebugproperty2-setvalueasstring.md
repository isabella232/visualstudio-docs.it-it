---
title: Proprietà IDebugProperty2::SetValueAsString . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721234"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Imposta il valore di una proprietà da una stringa specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametri
`pszValue`\
[in] Stringa contenente il valore da impostare.

`nRadix`\
[in] Radice da utilizzare nell'interpretazione di qualsiasi informazione numerica. Può essere 0 per tentare di determinare automaticamente la radice.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore. Nella tabella seguente vengono illustrati altri valori possibili.

|valore|Descrizione|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Impossibile convertire la stringa in un valore di proprietà oppure non è stato possibile impostare il valore della proprietà.|
|`E_SETVALUE_VALUE_IS_READONLY`|la proprietà è di sola lettura.|

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
