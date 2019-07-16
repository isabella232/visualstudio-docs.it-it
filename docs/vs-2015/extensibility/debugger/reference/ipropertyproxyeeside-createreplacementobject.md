---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147506"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea una copia di un oggetto dati specifico per l'analizzatore di espressioni (EE).  
  
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
 [in] Un' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto che contiene i dati da copiare.  
  
 `dataOut`  
 [out] Restituisce un nuovo `IEEDataStorage` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene specificato un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto che rappresenta una matrice di byte. Questo oggetto dati in entrata non è in genere implementato dal motore di esecuzione. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal motore di esecuzione, che consente di implementare EE il `IEEDataStorage` interfaccia su qualsiasi classe desiderata.  
  
 Si noti che i dati forniti da in ingresso `IEEDataStorage` oggetto debba essere gli stessi dati in uscita `IEEDataStorage` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
