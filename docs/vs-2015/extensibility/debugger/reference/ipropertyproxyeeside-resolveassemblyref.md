---
title: IPropertyProxyEESide::ResolveAssemblyRef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a3d8b5b41f8503a24d2a6d2643a1cf4c0290624
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527845"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IPropertyProxyEESide::ResolveAssemblyRef](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref).  
  
Determina la posizione del riferimento all'assembly gestito specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `assemName`  
 [in] Nome dell'assembly da risolvere.  
  
 `assemBytes`  
 [out] Restituisce un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i byte dell'assembly associati al riferimento.  
  
 `assemPdb`  
 [out] Restituisce un `IEEDataStorage` oggetto contenente il simbolo di archiviazione i dati associati a questo riferimento.  
  
 `assemLocation`  
 [out] Restituisce il percorso del riferimento.  
  
 `alr`  
 [out] Restituisce un valore di [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumerazione che indica la posizione di assembly questo riferimento del.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non viene in genere implementato da un analizzatore di espressioni personalizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
