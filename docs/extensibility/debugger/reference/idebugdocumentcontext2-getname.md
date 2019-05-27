---
title: IDebugDocumentContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec18ff6e906dd62383a7ff72dbb4502c7f8ba301
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204653"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Ottiene il nome visualizzabile del documento che contiene il contesto di questo documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>Parametri
`gnType`\
[in] Un valore compreso il [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumerazione che specifica il tipo del nome da restituire.

`pbstrFileName`\
[out] Restituisce il nome del file.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
Questo metodo in genere inoltra la chiamata per il [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) (metodo), a meno che il contesto del documento è scritto per archiviare il nome del documento stesso (come il programma di esempio).

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CDebugContext` oggetto che espone il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
