---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089518"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al profiler che si desidera interrompere la profilatura su tutti i motori di scripting applicabili. Con questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si arresta la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta alcun parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Profilatura non è stato possibile avviare.|  
|`S_FALSE`|Profilatura è stata arrestata quando uno script non è stato in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata.|  
  
## <a name="remarks"></a>Note  
 La chiamata a `IActiveScriptProfilerControl2::PrepareProfilerStop` assicura che vengano inviati gli eventi per le funzioni nello stack di chiamate. Questo metodo deve essere chiamato prima di arrestare la profilatura su qualsiasi motore di scripting che si trova nella scheda corrente. Il metodo può essere chiamato per qualsiasi motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)