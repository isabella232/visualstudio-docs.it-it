---
title: File di risposta MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71fdc29db3e2af66c85637648bb0703e7f7d80c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518371"
---
# <a name="msbuild-response-files"></a>File di risposta MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [file di risposta MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-response-files).  
  
  
I file di risposta (RSP) sono file di testo che contengono opzioni della riga di comando di MSBuild.exe. Ogni opzione può essere su una riga separata oppure tutte le opzioni possono essere sulla stessa riga. Le righe di commento sono precedute da un simbolo **#**. L'opzione **@** viene usata per passare un altro file di risposta a MSBuild.exe.  
  
 Il file di risposta automatica è un file RSP speciale che MSBuild.exe usa automaticamente quando si compila un progetto. Questo file, MSBuild.rsp, deve essere nella stessa directory di MSBuild.exe, in caso contrario non viene rilevato. È possibile modificare questo file per specificare opzioni predefinite della riga di comando per MSBuild.exe. Ad esempio, se si usa lo stesso logger ogni volta che si compila un progetto, è possibile aggiungere l'opzione **/logger** a MSBuild.rsp e MSBuild.exe userà il logger ogni volta che viene compilato un progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)



