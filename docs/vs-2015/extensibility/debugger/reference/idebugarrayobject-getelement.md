---
title: IDebugArrayObject::GetElement | Microsoft Docs
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
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20da5d4770ecfe36fcb52e3609ee28be38491e84
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764992"
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
 [in] L'indice di elemento.  
  
 `ppElement`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia che rappresenta l'elemento.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo considera tutti gli elementi di un oggetto matrice come una matrice unidimensionale, anche se l'oggetto di matrice è multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]` e una `dwIndex` parametro pari a 20, questo metodo restituisce l'elemento dal `myarray[1][1][2]`e un `dwIndex` restituisce l'elemento dal parametro di 21 `myarray[1][1][3]`. Usare la [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) metodo per determinare il numero totale di elementi nella matrice.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)

