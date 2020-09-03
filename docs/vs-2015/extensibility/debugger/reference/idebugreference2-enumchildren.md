---
title: 'IDebugReference2:: EnumChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4df5ad26db3ad519f162c62150d822ae2bc4b687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182476"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene un elenco di elementi figlio selezionati di un riferimento. Riservato per usi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 in Combinazione di flag dell'enumerazione [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) che specifica i campi nelle strutture [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) enumerate da compilare.  
  
 `dwRadix`  
 in La radice da usare per la formattazione di qualsiasi informazione numerica.  
  
 `dwAttribFilter`  
 in Combinazione di flag dell'enumerazione [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) utilizzata come filtro in combinazione con il `pszNameFilter` parametro per selezionare le strutture da enumerare.  
  
 `pszNameFilter`  
 in Stringa che specifica un filtro, ad esempio "MyX", usato in combinazione con il `dwAttribFilter` parametro per selezionare le strutture da enumerare.  
  
 `dwTimeout`  
 in Tempo massimo, in millisecondi, di attesa prima che venga restituito da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.  
  
 `ppEnum`  
 out Restituisce un oggetto [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) che contiene un elenco delle proprietà figlio richieste.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
