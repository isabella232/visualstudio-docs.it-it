---
title: IDiaEnumLineNumbers::get__NewEnum | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2f4749b8ada14daf6e8288e3a25712916c85143
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumlinenumbersgetnewenum"></a>IDiaEnumLineNumbers::get__NewEnum
Recupera il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pRetVal  
 [out] Restituisce il `IUnknown` interfaccia che rappresenta il <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versione di questo enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)