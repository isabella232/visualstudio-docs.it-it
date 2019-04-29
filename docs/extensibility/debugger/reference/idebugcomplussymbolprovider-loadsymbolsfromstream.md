---
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fb22dfdfb92b4955624a587a340d9f57eb2d59c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876520"
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Carica i simboli del flusso di dati di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LoadSymbolsFromStream(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStream(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    IStream pStream
);
```

#### <a name="parameters"></a>Parametri
`ulAppDomainID`

 [in] Identificatore del dominio dell'applicazione.

`guidModule`

 [in] Identificatore univoco del modulo.

`baseAddress`

 [in] Indirizzo di base di memoria.

`pUnkMetadataImport`

 [in] Oggetto che contiene i metadati del simbolo.

`pStream`

 [in] Flusso di dati che contiene i simboli.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **CDebugSymbolProvider** oggetto che espone le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfaccia. Il metodo chiama il [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) (metodo).

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IStream* pStream
)
{
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
