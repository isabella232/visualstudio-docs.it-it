---
title: IDiaSession::findInlineFramesByVA | Microsoft Docs
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee0f1ab711a36e0ad4291bd5ab96c5fa97fbd557
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806750"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client scorrere tutti i frame inline in un indirizzo virtuale specificato (valutazione della vulnerabilità).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `parent`  
 [in] Un `IDiaSymbol` oggetto che rappresenta l'elemento padre.  
  
 `va`  
 [in] Specifica l'indirizzo come un responsabile tecnologico  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumSymbols` oggetto che contiene l'elenco di frame che vengono recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



