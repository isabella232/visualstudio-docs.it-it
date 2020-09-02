---
title: 'IPropertyProxyEESide:: CreateReplacementObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147506"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (EE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dataIn`  
 in Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che contiene i dati da copiare.  
  
 `dataOut`  
 [out] Restituisce un nuovo oggetto `IEEDataStorage`.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 A questo metodo viene assegnato un oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che rappresenta una matrice di byte. Questo oggetto dati in ingresso non è in genere implementato da EE. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato da EE, che consente all'EE di implementare l' `IEEDataStorage` interfaccia su qualsiasi classe desiderata.  
  
 Si noti che i dati forniti dall'oggetto in ingresso `IEEDataStorage` devono essere gli stessi dati nell'oggetto in uscita `IEEDataStorage` .  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
