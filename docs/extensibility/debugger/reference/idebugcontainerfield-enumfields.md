---
title: Proprietà IDebugContainerField::EnumFields . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733231"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Crea un enumeratore per i campi del contenitore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parametri
`dwKindFilter`\
[in] Combinazione di costanti [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) che selezionano i campi da enumerare. I tipi di campo possono descrivere i tipi di archiviazione, ad esempio classe o primitiva, oppure informazioni specifiche, ad esempio il puntatore locale, il parametro o il puntatore "this".

`dwModifiersFilter`\
[in] Combinazione di costanti [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) che selezionano i campi da enumerare. I modificatori di campo possono essere autorizzazioni di accesso, ad esempio pubbliche o private, o informazioni di archiviazione, ad esempio virtuale, statica o finale.

`pszNameFilter`\
[in] Nome del campo da enumerare. Può essere un valore null se devono essere restituiti tutti i campi.

`nameMatch`\
[in] Valore dell'enumerazione [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) che controlla se la ricerca fa o meno distinzione tra maiuscole e minuscole.

`ppEnum`\
[fuori] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco di campi. Restituisce un valore null se non sono presenti campi.

## <a name="return-value"></a>Valore restituito
 Se riuscito, restituisce S_OK o S_FALSE se non sono presenti campi. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 I `dwKindFilter` `dwModifiersFilter`parametri `pszNameFilter` , e possono essere combinati, ad esempio, per selezionare tutti i metodi virtuali pubblici denominati "MyMethod".

## <a name="see-also"></a>Vedere anche
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
