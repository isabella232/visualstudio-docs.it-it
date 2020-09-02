---
title: 'IDiaPropertyStorage:: enum | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48b289ed1e376f224ec513e7a118691d75fc9b69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538846"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ottiene un enumeratore per le proprietà all'interno di questo set.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppenum`  
 out Restituisce un `IEnumSTATPROPSTG` oggetto (nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop) che rappresenta un'enumerazione delle proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
