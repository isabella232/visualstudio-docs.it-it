---
title: 'IPerPropertyBrowsing2:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576765"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Consente al chiamante di compilare una casella di riepilogo con una matrice conteggiata di puntatori di stringa che rappresentano i valori potenziali per questa proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dispid`  
 in Identificatore di invio della proprietà per cui il chiamante richiede l'elenco di stringhe.  
  
 `pCaStrings`  
 out Puntatore a una struttura di matrice conteggiata allocata dal chiamante che contiene il numero di elementi e l'indirizzo di una matrice allocata dal metodo di puntatori di stringa. Se il metodo ha esito negativo, non viene allocata memoria e il contenuto della struttura non è definito.  
  
 `pCaCookies`  
 out Puntatore alla struttura di matrice conteggiata allocata dal chiamante che contiene il numero di elementi e l'indirizzo di una matrice di DWORD allocata dal metodo. Se il metodo ha esito negativo, non viene allocata memoria e il contenuto della struttura non è definito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un `HRESULT` valido, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)