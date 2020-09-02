---
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423686"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene un elemento della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwIndex`  
 in Indice dell'elemento.  
  
 `ppElement`  
 out Restituisce un'interfaccia [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'elemento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo considera tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale. Ad esempio, data la matrice `myarray[3][2][6]` e un `dwIndex` parametro di 20, questo metodo restituisce l'elemento da `myarray[1][1][2]` e un `dwIndex` parametro di 21 restituisce l'elemento da `myarray[1][1][3]` . Usare il metodo [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) per determinare il numero totale di elementi nella matrice.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
