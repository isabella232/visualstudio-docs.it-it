---
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199510"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i nuovi dati dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataIn`  
 in Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che contiene i nuovi dati.  
  
 `dataOut`  
 out Restituisce un nuovo `IEEDataStorage` oggetto contenente i dati sostituiti.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo aggiorna effettivamente i dati dell'oggetto. I dati nell'oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) restituito non devono necessariamente corrispondere ai dati nell'oggetto in arrivo `IEEDataStorage` , ma l'oggetto restituito deve riflettere il valore corrente della proprietà.  
  
 L'oggetto dati in ingresso non è in genere implementato da EE. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato da EE, che consente all'EE di implementare l' `IEEDataStorage` interfaccia su qualsiasi classe desiderata.  
  
 Il metodo [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un oggetto dati basato sull'oggetto dati in ingresso ma non influisce sui dati originali della proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
