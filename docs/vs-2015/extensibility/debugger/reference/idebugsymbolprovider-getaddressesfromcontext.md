---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
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
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28ba5c25a5e895d9e2eb403f2688961ec8e36edf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519361"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugSymbolProvider::GetAddressesFromContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext).  
  
Questo metodo esegue il mapping di un contesto di documento in una matrice di indirizzi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocContext`  
 [in] Il contesto del documento.  
  
 `fStatmentOnly`  
 [in] Se TRUE, limita gli indirizzi di debug per una singola istruzione.  
  
 `ppEnumBegAddresses`  
 [out] Restituisce un enumeratore per gli indirizzi iniziali di debug associato con questa istruzione o la riga.  
  
 `ppEnumEndAddresses`  
 [out] Restituisce un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumeratore per gli indirizzi di debug finale associati a questa istruzione o la riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un contesto di documento in genere indica un intervallo di righe di origine. Questo metodo fornisce il valore iniziale e finale debug indirizzi associati con queste righe. Alcuni linguaggi viene consentita istruzioni che si estendono su più righe o le righe che contiene più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug per una singola istruzione.  
  
 È possibile che una singola istruzione per disporre di più indirizzi di debug, come nel caso di modelli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

