---
title: IDebugProgramNode2::GetProgramName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9af930716725a62fff5ea3d1635b506b06b26086
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721993"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Ottiene il nome del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Parametri
`pbstrProgramName`\
[fuori] Restituisce il nome del programma.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Il nome di un programma non è la stessa cosa come il percorso del programma, anche se il nome del programma può essere parte di tale percorso.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CProgram` implementare questo metodo per un oggetto semplice che implementa il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia. La `MakeBstr` funzione alloca una copia della stringa specificata come BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
