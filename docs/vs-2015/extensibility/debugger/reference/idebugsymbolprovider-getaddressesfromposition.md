---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71691c2c9abe6723cf852738fa66be0ea45aeda7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812218"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo esegue il mapping di una posizione di documento in una matrice di indirizzi di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pDocPos`  
 [in] Posizione del documento.  
  
 `fStatmentOnly`  
 [in] Se TRUE, limita gli indirizzi di debug per una singola istruzione.  
  
 `ppEnumBegAddresses`  
 [out] Restituisce un enumeratore per gli indirizzi iniziali di debug associato con questa istruzione o la riga.  
  
 `ppEnumEndAddresses`  
 [out] Restituisce un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumeratore per gli indirizzi di debug finale associati a questa istruzione o la riga.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Una posizione del documento indica in genere un intervallo di righe di origine. Questo metodo fornisce il valore iniziale e finale debug indirizzi associati con queste righe. Alcuni linguaggi viene consentita istruzioni che si estendono su più righe o le righe che contiene più di un'istruzione. Questo metodo fornisce un flag per limitare gli indirizzi di debug per una singola istruzione.  
  
 È possibile che una singola istruzione per disporre di più indirizzi di debug, come nel caso di modelli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

