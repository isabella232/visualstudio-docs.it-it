---
title: Attività Message | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190898"
---
# <a name="message-task"></a>Attività Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Registra un messaggio durante una compilazione.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Message`.  
  
|Parametro|DESCRIZIONE|  
|---------------|-----------------|  
|`Importance`|Parametro `String` facoltativo.<br /><br /> Specifica l'importanza del messaggio. Il valore di questo parametro può essere `high`, `normal` o `low`. Il valore predefinito è `normal`.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Testo dell'errore da registrare.|  
  
## <a name="remarks"></a>Osservazioni  
 L'attività `Message` consente ai progetti [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di inviare messaggi ai logger in fasi diverse del processo di compilazione.  
  
 Se il parametro `Condition` restituisce `true`, verrà registrato il valore del parametro `Text` e la compilazione continuerà a essere eseguita. Se il parametro `Condition` non esiste, verrà registrato il testo del messaggio. Per altre informazioni sulla registrazione, vedere [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione).  
  
 Per impostazione predefinita, il messaggio viene inviato al logger di console di MSBuild. Questo comportamento può essere modificato impostando il parametro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. Il parametro `Importance` viene interpretato dal logger.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito i messaggi vengono registrati in tutti i logger registrati.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione)
