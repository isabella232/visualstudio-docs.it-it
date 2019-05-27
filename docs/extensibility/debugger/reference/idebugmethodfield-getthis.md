---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3e88f209b506d8baf10a779d282a78122c274fb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211929"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ottiene il `this` (`Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) puntatore dell'oggetto che contiene il metodo.

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
[out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che rappresenta il puntatore "this".

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Linguaggi orientati, prevede in genere un puntatore implicito per la creazione dell'istanza corrente di una classe. Questo è noto come `this` in c# o C++ sia come `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Vedere anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)