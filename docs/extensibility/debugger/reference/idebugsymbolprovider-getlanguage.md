---
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfa11a1df6460c08431d7b23fabe5d94674baad2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347608"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Questo metodo ottiene il linguaggio utilizzato per compilare il codice in corrispondenza dell'indirizzo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
[in] Un oggetto indirizzo rappresentato da un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

`pguidLanguage`\
[out] Restituisce un `GUID` che specifica la lingua.

`pguidLanguageVendor`\
[out] Restituisce un `GUID` che specifica il fornitore di linguaggio.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il motore di debug chiama questo metodo per ottenere le informazioni necessarie per selezionare l'analizzatore di espressioni corretto.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)