---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49874de9166310fc4b9a887fd1fc6d6355682c7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942686"
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
  
#### <a name="parameters"></a>Parametri  
 `dwKindFilter`  
 [in] Una combinazione di [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) le costanti che selezionano i campi da enumerare. Tipi di campo possono descrivere i tipi di archiviazione, ad esempio informazioni primitive o specifiche o classe, ad esempio locale, un parametro o puntatore "this".  
  
 `dwModifiersFilter`  
 [in] Una combinazione di [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) le costanti che selezionano i campi da enumerare. Modificatori di campo possono essere le autorizzazioni di accesso, ad esempio pubblico o privato o informazioni sull'archiviazione, ad esempio virtual, static o finale.  
  
 `pszNameFilter`  
 [in] Il nome del campo da enumerare. Può trattarsi di un valore null se tutti i campi devono essere restituiti.  
  
 `nameMatch`  
 [in] Un valore compreso il [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumerazione che controlla se la ricerca è distinzione maiuscole/minuscole o No.  
  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco dei campi. Restituisce un valore null se non sono presenti campi.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK o S_FALSE se non sono presenti campi. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `dwKindFilter`, `dwModifiersFilter`, e `pszNameFilter` parametri possono essere combinati, ad esempio, per selezionare tutti i metodi pubblici virtuali denominati "MyMethod".  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)