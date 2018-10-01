---
title: Get_lasterror | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abe45a8d86361c3bb3af458ca1352fb269dbd82d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530248"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Get_lasterror](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-get-lasterror).  
  
Recupera il nome del file per l'ultimo errore di caricamento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce una stringa che contiene il nome del file con estensione pdb associato con l'ultimo errore di caricamento.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce l'ultimo codice di errore causato da un'operazione di caricamento. Restituisce `E_INVALIDARG` se il `pRetVal` parametro è `NULL`.  
  
## <a name="example"></a>Esempio  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



