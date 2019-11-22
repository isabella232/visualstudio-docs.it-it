---
title: Attività SetEnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc9b15efb8fca12382fae94912d22c39b96bd4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295971"
---
# <a name="setenv-task"></a>Attività SetEnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Imposta o elimina il valore di una variabile di ambiente specificata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **SetEnv**.  
  
|Parametro|DESCRIZIONE|  
|---------------|-----------------|  
|**Name**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|  
|**OutputEnvironmentVariable**|Parametro di output **String** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|  
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima del valore della variabile di ambiente specificato dal parametro **Name** e quindi assegna il risultato alla variabile di ambiente. Se `false`, assegna solo il valore del parametro **Value** alla variabile di ambiente.|  
|**Destinazione**|Parametro **String** facoltativo.<br /><br /> Specifica il percorso di archiviazione di una variabile di ambiente. Specificare "`User`" o "`Machine`".<br /><br /> Per altre informazioni, vedere "Enumerazione EnvironmentVariableTarget" sul sito Web [MSDN](https://go.microsoft.com/fwlink/?LinkId=737).|  
|**Valore**|Parametro **String** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**. Se **Value** è vuoto e la variabile esiste, la variabile viene eliminata. Se la variabile non esiste, non si verifica alcun errore anche se non è possibile eseguire l'operazione.<br /><br /> Per altre informazioni, vedere "Metodo Environment::SetEnvironmentVariable" sul sito Web [MSDN](https://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle attività](../msbuild/msbuild-task-reference.md)
