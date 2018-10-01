---
title: IDebugTypeFieldBuilder::CreatePointerToType | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7563c8597a0b19e7fbe144a773500eccbbe7b0e0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527789"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugTypeFieldBuilder::CreatePointerToType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype).  
  
Crea un puntatore al tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```csharp  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pTypeField`  
 [in] Tipo in modo che punti. È rappresentato dal [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia.  
  
 `pPtrToTypeField`  
 [out] Restituisce il puntatore rappresentato da una nuova **IDebugField** oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)

