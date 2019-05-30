---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16d352ae5397d786c5d77f56a513e9ae2db2d7b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348835"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la stringa associata a questa proprietà e lo archivia in un buffer fornito dall'utente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parametri
`buflen`\
[in] Numero massimo di caratteri può contenere il buffer fornito dall'utente.

`rgString`\
[out] Restituisce la stringa.

 [C++ solo], `rgString` è un puntatore a un buffer che riceve i caratteri Unicode della stringa. Questo buffer deve essere almeno `buflen` caratteri (non byte) nella dimensione.

`pceltFetched`\
[out] In cui viene restituito il numero di caratteri effettivamente archiviati nel buffer. (Può essere `NULL` in C++.)

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
In C++, prestare attenzione per assicurarsi che il buffer è almeno `buflen` caratteri Unicode. Si noti che un carattere Unicode è la lunghezza di 2 byte.

> [!NOTE]
> In C++, la stringa restituita non include un carattere di terminazione null. Se non specificato, `pceltFetched` specificherà il numero di caratteri nella stringa.

## <a name="example"></a>Esempio

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Vedere anche
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
