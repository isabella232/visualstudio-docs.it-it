---
title: Proprietà IDebugProperty3::GetStringChars . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721089"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la stringa associata a questa proprietà e la archivia in un buffer fornito dall'utente.

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
[in] Numero massimo di caratteri che il buffer fornito dall'utente può contenere.

`rgString`\
[fuori] Restituisce la stringa.

 È disponibile solo `rgString` un puntatore a un buffer che riceve i caratteri Unicode della stringa. Questo buffer deve `buflen` avere una dimensione di almeno caratteri (non byte).

`pceltFetched`\
[fuori] Dove viene restituito il numero di caratteri effettivamente archiviati nel buffer. (Può `NULL` essere in C.

## <a name="return-value"></a>Valore restituito
Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
È necessario prestare attenzione a garantire che il buffer `buflen` sia lungo almeno caratteri Unicode. Si noti che un carattere Unicode è lungo 2 byte.

> [!NOTE]
> La stringa restituita non include un carattere di terminazione null. Se specificato, `pceltFetched` verrà specificato il numero di caratteri nella stringa.

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
