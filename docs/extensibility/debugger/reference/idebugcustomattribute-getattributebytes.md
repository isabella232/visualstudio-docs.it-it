---
title: IDebugCustomAttribute::GetAttributeBytes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5aa1713aba2def384a9dd8290d6ae6afcee6ba64
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913234"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Ottiene le informazioni sugli attributi come un blob di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppBlob`  
 [in, out] Matrice che viene compilata con i byte di attributo.  
  
 `pdwLen`  
 [in, out] Specifica il numero massimo di byte da restituire nel `ppBlob` della matrice e restituisce il numero di byte effettivamente scritti nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Impostare il `ppBlob` attributi di parametro con un valore null per restituire il numero di byte disponibili. Quindi allocare una matrice e passare la matrice in per il `ppBlob` parametro.  
  
 I byte di attributo rappresentano i dati non elaborati dell'attributo personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)