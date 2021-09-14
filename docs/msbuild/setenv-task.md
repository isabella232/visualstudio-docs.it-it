---
title: Attività SetEnv | Microsoft Docs
description: Informazioni su MSBuild'attività SetEnv per impostare o eliminare il valore di una variabile di ambiente specificata.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
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
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c760e22842a3063036d0e4f8c2945ddefc312900
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625554"
---
# <a name="setenv-task"></a>Attività SetEnv

Imposta o elimina il valore di una variabile di ambiente specificata.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività **SetEnv**.

|Parametro|Descrizione|
|---------------|-----------------|
|**Nome**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|
|**OutputEnvironmentVariable**|Parametro di output **String** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima del valore della variabile di ambiente specificato dal parametro **Name** e quindi assegna il risultato alla variabile di ambiente. Se `false`, assegna solo il valore del parametro **Value** alla variabile di ambiente.|
|**Destinazione**|Parametro **String** facoltativo.<br /><br /> Specifica il percorso di archiviazione di una variabile di ambiente. Specificare "Utene" o "Computer".<br /><br /> Per altre informazioni, vedere [Enumerazione EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Valore**|Parametro **String** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**. Se **Value** è vuoto e la variabile esiste, la variabile viene eliminata. Se la variabile non esiste, non si verifica alcun errore anche se non è possibile eseguire l'operazione.<br /><br /> Per altre informazioni, vedere [Metodo Environment::SetEnvironmentVariable](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
