---
title: Get_backendmajor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf32104654d40f314dc3468eaf28dfded6998df9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942309"
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
Recupera il numero di versione principale di back-end del compilatore.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_backEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di versione principale di back-end. Vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Un compilatore è in genere costituito da due elementi principali: il front-end (parser), che gestisce l'analisi del codice sorgente in un modulo intermedio, e un back-end (Generatore di codice), che converte il formato intermedio in assembly. Non è insolito per il front-end avere una versione diversa rispetto al back-end.  
  
 Un front-end o un numero di versione back-end è costituito da tre parti: \<principale >.\< secondaria >. \<compilazione >, dove \<principali > è il numero di versione principale, \<secondaria > è il numero di versione secondaria, e \<compilazione > è il numero di build. Ad esempio, 13.10.3077.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)