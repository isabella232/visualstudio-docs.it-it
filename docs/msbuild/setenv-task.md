---
title: Attività SetEnv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2d9cec2c76b2159e14b1e7abe19b93ab91f6688
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153774"
---
# <a name="setenv-task"></a>Attività SetEnv
Imposta o elimina il valore di una variabile di ambiente specificata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività **SetEnv**.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Name**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|  
|**OutputEnvironmentVariable**|Parametro di output **String** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|  
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima del valore della variabile di ambiente specificato dal parametro **Name** e quindi assegna il risultato alla variabile di ambiente. Se `false`, assegna solo il valore del parametro **Value** alla variabile di ambiente.|  
|**Destinazione**|Parametro **String** facoltativo.<br /><br /> Specifica il percorso di archiviazione di una variabile di ambiente. Specificare "Utene" o "Computer".<br /><br /> Per altre informazioni, vedere [Enumerazione EnvironmentVariableTarget](https://msdn.microsoft.com/library/system.environmentvariabletarget(v=vs.110).aspx) sul sito Web MSDN.|  
|**Valore**|Parametro **String** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**. Se **Value** è vuoto e la variabile esiste, la variabile viene eliminata. Se la variabile non esiste, non si verifica alcun errore anche se non è possibile eseguire l'operazione.<br /><br /> Per altre informazioni, vedere [Metodo Environment::SetEnvironmentVariable](https://msdn.microsoft.com/library/96xafkes(v=vs.110).aspx) sul sito Web MSDN.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)