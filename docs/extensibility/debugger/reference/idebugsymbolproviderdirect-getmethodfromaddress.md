---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76bec7cb621605933f8cc0b15ff6cb6e4dd6d70e
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224004"
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

 [in] Eseguire il debug indirizzo rappresentato dal [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

 `pGuid`\

 [out] Identificatore univoco del modulo.

 `pAppID`\

 [out] Identificatore del dominio dell'applicazione.

 `pTokenClass`\

 [out] Token che rappresenta la classe che lo contiene.

 `pTokenMethod`\

 [out] Token che rappresenta il modulo.

 `pdwOffset`\

 [out] Offset in byte dall'inizio del `pAddress` parametro.

 `pdwVersion`\

 [out] Numero di versione del metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)