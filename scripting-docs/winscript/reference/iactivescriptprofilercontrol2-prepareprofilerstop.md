---
title: IActiveScriptProfilerControl2::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571439"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al profiler che si intende arrestare la profilatura su tutti i motori di scripting applicabili. Utilizzando questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si arresta la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Non è stato possibile avviare la profilatura.|  
|`S_FALSE`|La profilatura è stata interrotta quando uno script non è in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La profilatura non è abilitata.|  
  
## <a name="remarks"></a>Note  
 La chiamata di `IActiveScriptProfilerControl2::PrepareProfilerStop` garantisce che vengano inviati gli eventi per le funzioni nello stack di chiamate. Questo metodo deve essere chiamato prima di arrestare la profilatura in un motore di script che si trova nella scheda corrente. Il metodo può essere chiamato per qualsiasi motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)  
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)