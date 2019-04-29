---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 30419e20b6ac1519e3d9b278aabfcb012372d193
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923754"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il numero di elementi nella matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwElements`  
 [out] Restituisce il conteggio.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo considera tutti gli elementi di un oggetto matrice come una matrice unidimensionale, anche se l'oggetto di matrice è multidimensionale. Si consideri ad esempio la matrice `myarray[3][2][6]`, questo metodo restituirà 36 nel `pdwElements` parametro. Usare la [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metodo per recuperare i singoli elementi uno alla volta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
