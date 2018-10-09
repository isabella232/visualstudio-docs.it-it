---
title: Comando Registra output finestra di comando | Microsoft Docs
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
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f6cdef31ec8988612815a76c30198e97ddf4c26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533105"
---
# <a name="log-command-window-output-command"></a>Comando Registra output finestra di comando
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [finestra di comando registra Output comando](https://docs.microsoft.com/visualstudio/ide/reference/log-command-window-output-command).  
  
  
Copia interamente l'input e l'output della finestra di **comando** in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Facoltativo. Nome del file di log. Per impostazione predefinita, il file viene creato nella cartella del profilo dell'utente. Se il nome del file specificato esiste già, il log viene accodato alla fine del file esistente. Se non viene specificato alcun file, viene usato l'ultimo file specificato. Se non esiste alcun file precedente, viene creato un file di log predefinito, denominato cmdline.log.  
  
> [!TIP]
>  Per modificare il percorso in cui viene salvato il file di log, immettere il percorso completo del file, racchiuso tra virgolette se il percorso contiene spazi.  
  
## <a name="switches"></a>Opzioni  
 /on  
 Facoltativo. Avvia la registrazione per la finestra di **comando** nel file specificato e accoda il file con le nuove informazioni.  
  
 /off  
 Facoltativo. Interrompe la registrazione per la finestra di **comando**.  
  
 /overwrite  
 Facoltativo. Se il file specificato nell'argomento `filename` corrisponde a un file esistente, il file viene sovrascritto.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato alcun file, viene creato per impostazione predefinita il file cmdline.log. Per impostazione predefinita, l'alias per questo comando è Log.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene creato un nuovo file di log, cmdlog, e viene avviata la registrazione dei comandi.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Questo esempio arresta la registrazione dei comandi.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Questo esempio consente di riprendere la registrazione dei comandi nel file di log usato in precedenza.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)


