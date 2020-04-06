---
title: IDebugMethodField::GetThis Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727173"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ottiene `this` il`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]puntatore in ( in ) dell'oggetto contenente il metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametri
`ppClass`\
[fuori] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che rappresenta il puntatore "this".

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Nei linguaggi orientati agli oggetti, è in genere un puntatore implicito alla creazione di istanze corrente di una classe. Questa operazione `this` è nota come in `Me` C, C, e come in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
