---
title: Comando Apri soluzione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c2c93f44ba7c801b31390c411da1d16c1645bf6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517208"
---
# <a name="open-solution-command"></a>Comando Apri soluzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [comando Apri soluzione](https://docs.microsoft.com/visualstudio/ide/reference/open-solution-command).  
  
  
Apre una soluzione esistente, chiudendo tutte le altre soluzioni aperte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `Filename`  
 Obbligatorio. Il percorso completo e nome file della soluzione da aprire.  
  
 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aperta la soluzione Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



