---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537355"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera i nomi di stringa corrispondenti per gli identificatori di proprietà specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpropid`  
 in Numero di ID di proprietà in `rgpropid` .  
  
 `rgpropid`  
 in Matrice di ID di proprietà per cui ottenere i nomi ( `PROPID` è definito in Wtypes. h come `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Matrice di nomi di proprietà per gli ID di proprietà specificati. La matrice deve essere pre-allocata per contenere il numero richiesto di nomi di proprietà e deve essere in grado di contenere almeno `cpropid``BSTR` stringhe.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 I nomi di proprietà restituiti devono essere liberati (chiamando la `SysFreeString` funzione) quando non sono più necessari.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
