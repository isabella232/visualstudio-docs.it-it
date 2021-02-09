---
title: 'IDebugSymbolProvider:: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 120434e44819d4c503336dffeaa1c255626270d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880229"
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
in Oggetto Address rappresentato da un'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pguidLanguage`\
out Restituisce un oggetto `GUID` che specifica la lingua.

`pguidLanguageVendor`\
out Restituisce un oggetto `GUID` che specifica il fornitore del linguaggio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il motore di debug chiama questo metodo per ottenere le informazioni necessarie per selezionare l'analizzatore di espressioni corretto.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
