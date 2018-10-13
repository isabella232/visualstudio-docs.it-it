---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26d4a913bc6ae0ee87b018ac40757994e9c06e6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233753"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta il valore di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Un valore compreso il [enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica il registro in cui scrivere.  
  
 `NewVal`  
 [in] Il valore di nuovo Registra.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Nonostante le dimensioni del valore, un'implementazione deve archiviare solo registro in genere conserva. Ad esempio, un registro a 8 bit deve conservare solo i bit più bassi 8-del valore specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)



