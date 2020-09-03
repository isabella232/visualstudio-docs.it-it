---
title: 'IDebugSymbolProviderDirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a062056f4a61521966417e9923a17f6d85b991a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718928"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Recupera le informazioni sul metodo in corrispondenza dell'indirizzo di debug specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
in Indirizzo di debug rappresentato dall'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pGuid`\
out Identificatore univoco del modulo.

`pAppID`\
out Identificatore del dominio dell'applicazione.

`pTokenClass`\
out Token che rappresenta la classe che lo contiene.

`pTokenMethod`\
out Token che rappresenta il modulo.

`pdwOffset`\
out Offset in byte dall'inizio del `pAddress` parametro.

`pdwVersion`\
out Numero di versione del metodo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
