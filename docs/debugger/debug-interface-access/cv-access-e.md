---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 373149884078b58926493fd7f37756ddb4eb8829
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838755"
---
# <a name="cvaccesse"></a>CV_access_e
Specifica l'ambito di visibilità (livello di accesso) di funzioni membro e variabili.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)