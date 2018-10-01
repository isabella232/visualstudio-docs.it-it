---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
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
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d806eec4d5d03b3ac589cca2de5dd6146231723
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532523"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IPropertyProxyEESide::InPlaceUpdateObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject).  
  
Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i dati dell'oggetto nuovo.  
  
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
 [in] Un' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i nuovi dati.  
  
 `dataOut`  
 [out] Restituisce un nuovo `IEEDataStorage` oggetto contenente i dati sostituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiorna effettivamente i dati dell'oggetto. I dati nell'oggetto restituito [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto non deve essere quello utilizzato per i dati in ingresso `IEEDataStorage` oggetto, ma l'oggetto restituito deve riflettere il valore della proprietà corrente.  
  
 L'oggetto dati in entrata non è in genere implementato dal motore di esecuzione. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal motore di esecuzione, che consente di implementare EE il `IEEDataStorage` interfaccia su qualsiasi classe desiderata.  
  
 Il [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metodo crea un oggetto dati in base all'oggetto dati in ingresso, ma influisce sui dati originali della proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

