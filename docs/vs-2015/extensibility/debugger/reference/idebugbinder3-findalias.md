---
title: IDebugBinder3::FindAlias | Microsoft Docs
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
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d638ed77b2ddcab54431862a26cdbab8a356e4ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528236"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugBinder3::FindAlias](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-findalias).  
  
Questo metodo individua un alias, dato un nome. Si eseguirà la ricerca tutti gli alias nel programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcstrName`  
 [in] Nome di alias da trovare.  
  
 `ppAlias`  
 [out] Alias (se presente) rappresentato dal [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` (se non viene trovato alias) o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo inizializza l'oggetto di destinazione a null prima di chiamare il metodo. quindi verifica un valore null in un secondo momento determinare se l'alias è stato trovato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

