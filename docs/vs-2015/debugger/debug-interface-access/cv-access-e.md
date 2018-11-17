---
title: CV_access_e | Microsoft Docs
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
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4491aa77eaf27915dcda1654ef00dca351804ff1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745649"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica l'ambito di visibilità (livello di accesso) di funzioni membro e variabili.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementi  
 CV_private  
 Membro dispone di accesso privato.  
  
 CV_protected  
 Membro con l'accesso protetto.  
  
 CV_public  
 Membro dispone di accesso pubblico.  
  
## <a name="remarks"></a>Note  
 Il `friend` identificatore di accesso non viene incluso qui perché è in genere usato dalle funzioni non membro che dispongono dell'accesso agli elementi privati e protetti della classe. Usare la [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodo per individuare i simboli con `SymTagFriend` accesso.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)



