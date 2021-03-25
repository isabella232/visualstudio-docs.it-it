---
description: 'IDebugProgramNode2:: getprogramname ottiene il nome del programma.'
title: 'IDebugProgramNode2:: getprogrammname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 376054406d0c127a0bbdcd5ee0a90bc694f9cd02
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087236"
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
out Restituisce il nome del programma.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Il nome di un programma non corrisponde al percorso del programma, sebbene il nome del programma possa essere parte di tale percorso.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un `CProgram` oggetto semplice che implementa l'interfaccia [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . La `MakeBstr` funzione alloca una copia della stringa specificata come BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
