---
title: Metodo marker_series::write_flag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f70f6b357e8baaf721c751c57b21924afaff90e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069779"
---
# <a name="markerserieswriteflag-method"></a>Metodo marker_series::write_flag
Scrive un flag nel file di traccia del visualizzatore di concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `_Format`  
 Stringa di formato composta che contiene testo combinato con zero o più elementi di formato, che corrispondono agli oggetti nell'elenco degli argomenti.  
  
 `_Importance`  
 Livello di importanza.  
  
 `_Category`  
 Categoria.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** *cvmarkersobj.h*  
  
 **Spazio dei nomi:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vedere anche  
 [Classe marker_series](../profiling/marker-series-class.md)