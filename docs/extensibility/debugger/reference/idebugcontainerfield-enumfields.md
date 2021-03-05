---
description: Crea un enumeratore per i campi del contenitore.
title: 'IDebugContainerField:: EnumFields | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ec12cd97318fc41b97c5a7701dff2346524101
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143168"
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
in Combinazione di [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) costanti che selezionano i campi da enumerare. I tipi di campo possono descrivere i tipi di archiviazione, ad esempio la classe o la primitiva, o informazioni specifiche, ad esempio il puntatore locale, il parametro o il puntatore "This".

`dwModifiersFilter`\
in Combinazione di [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) costanti che selezionano i campi da enumerare. I modificatori di campo possono essere autorizzazioni di accesso, ad esempio pubbliche o private, o informazioni di archiviazione, ad esempio virtuale, statica o finale.

`pszNameFilter`\
in Nome del campo da enumerare. Può trattarsi di un valore null se devono essere restituiti tutti i campi.

`nameMatch`\
in Valore dell'enumerazione [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) che controlla se la ricerca fa distinzione tra maiuscole e minuscole.

`ppEnum`\
out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco dei campi. Restituisce un valore null se non sono presenti campi.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o S_FALSE se non sono presenti campi. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 `dwKindFilter` `dwModifiersFilter` `pszNameFilter` È possibile combinare i parametri, e, ad esempio, per selezionare tutti i metodi virtuali pubblici denominati "MyMethod".

## <a name="see-also"></a>Vedi anche
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
