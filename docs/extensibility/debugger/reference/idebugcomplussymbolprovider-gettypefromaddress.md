---
title: IDebugComPlusSymbolProvider::GetTypeFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetTypeFromAddress
- GetTypeFromAddress
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9670dd1c6c56e2e6b983dffc054aa23fddae6e09
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206267"
---
# <a name="idebugcomplussymbolprovidergettypefromaddress"></a>IDebugComPlusSymbolProvider::GetTypeFromAddress
Recupera in un tipo di simbolo dato il relativo indirizzo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetTypeFromAddress(
    IDebugAddress* pAddress,
    IDebugField**  ppField
);
```

```csharp
int GetTypeFromAddress(
    IDebugAddress   pAddress,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
[in] L'indirizzo di debug che è rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

`ppField`\
[out] Restituisce il tipo di matrice come rappresentato da un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interfaccia.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia.

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromAddress(
    IDebugAddress *pAddress,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromPrimitive );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    switch ( da.addr.dwKind )
    {
        case ADDRESS_KIND_METADATA_LOCAL:
        case ADDRESS_KIND_METADATA_PARAM:
        case ADDRESS_KIND_METADATA_FIELD:
        case ADDRESS_KIND_METADATA_ARRAYELEM:
        case ADDRESS_KIND_METADATA_METHOD:
            {
                IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                break;
            }

        case ADDRESS_KIND_METADATA_RETVAL:
            {
                if ( da.addr.addr.addrRetVal.dwCorType )
                {

                    IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );
                    IfFailGo( this->CreateType((const COR_SIGNATURE*)(&da.addr.addr.addrRetVal.rgSig),
                                               da.addr.addr.addrRetVal.dwSigSize,
                                               da.GetModule(),
                                               mdMethodDefNil,
                                               pGenScope,
                                               ppField) );
                }
                else
                {
                    IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                }

                break;
            }

        default:
            {
                ASSERT(!"Address type not supported.");
            }
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromPrimitive, hr );

    RELEASE( pGenScope );

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
