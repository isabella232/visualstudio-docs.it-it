---
title: IDiaSectionContrib::get_compilandId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compilandId method
ms.assetid: 71ef2e63-d095-42b6-88d8-626e3129f0d9
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a42cda74c5ca4bd2b5a4552787422b07b32287
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965638"
---
# <a name="idiasectioncontribgetcompilandid"></a>IDiaSectionContrib::get_compilandId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera l'identificatore del modulo nella sezione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce l'identificatore del modulo per la sezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
