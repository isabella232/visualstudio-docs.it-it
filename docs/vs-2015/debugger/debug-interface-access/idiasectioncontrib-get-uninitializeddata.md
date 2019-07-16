---
title: IDiaSectionContrib::get_uninitializedData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_uninitializedData method
ms.assetid: 39736f35-6c73-4f54-a092-517192e417ff
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ee0f9dd959d22d064ef2a1f86bae7789179ed3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151857"
---
# <a name="idiasectioncontribgetuninitializeddata"></a>IDiaSectionContrib::get_uninitializedData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che indica se la sezione contiene dati non inizializzati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_uninitializedData (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se la sezione contiene dati non inizializzati; in caso contrario, restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
