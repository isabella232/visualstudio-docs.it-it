---
title: Attività Warning | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93ac5f92f5912827a0ff73dcb21dd7ea8294b684
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517874"
---
# <a name="warning-task"></a>Attività Warning
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività Warning](https://docs.microsoft.com/visualstudio/msbuild/warning-task).  
  
  
Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Warning`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Code`|Parametro `String` facoltativo.<br /><br /> Il codice di avviso da associare all'avviso.|  
|`File`|Parametro `String` facoltativo.<br /><br /> Specifica il file pertinente, se presente. Se non viene indicato alcun file, verrà usato il file contenente l'attività Warning.|  
|`HelpKeyword`|Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'avviso.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Il testo dell'avviso registrato da [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] se il parametro `Condition` restituisce `true`.|  
  
## <a name="remarks"></a>Note  
 L'attività `Warning` consente ai progetti [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] di verificare la presenza di una configurazione o una proprietà richiesta prima di procedere con il passaggio successivo della compilazione.  
  
 Se il parametro `Condition` dell'attività `Warning` restituisce `true`, verrà registrato il valore del parametro `Text` e l'esecuzione della compilazione continua. Se non esiste un parametro `Condition`, viene registrato il testo dell'avviso. Per altre informazioni sulla registrazione, vedere [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione).  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene verificata la presenza di proprietà impostate nella riga di comando. Se non sono presenti proprietà impostate, il progetto genera un evento di avviso e registra il valore del parametro `Text` dell'attività `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md)  (Recupero di log di compilazione)  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)



