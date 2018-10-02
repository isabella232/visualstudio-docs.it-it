---
title: -Log (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfd6d9ac2493e4caca95538140fb9af78db8e074
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520260"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [-Log (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/log-devenv-exe).  
  
  
Registra tutte le attività nel file di log per la risoluzione dei problemi. Il file verrà visualizzato dopo aver chiamato `devenv /log` almeno una volta. Per impostazione predefinita, il file di log è:  
  
 *%APPDATA%* \Microsoft\VisualStudio\\*Versione*\ActivityLog.xml  
  
 dove *Versione* indica la versione di Visual Studio. È tuttavia possibile specificare un percorso e un nome di file diversi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /log Path\NameOfLogFile  
```  
  
## <a name="remarks"></a>Note  
 Questa opzione deve apparire alla fine della riga di comando, dopo tutte le altre opzioni.  
  
 Il log viene scritto per tutte le istanze di Visual Studio richiamate con l'opzione /log. Non vengono registrate le istanze di Visual Studio richiamate senza l'opzione /log.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



