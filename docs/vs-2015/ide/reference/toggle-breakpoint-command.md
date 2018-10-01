---
title: Comando Imposta/Rimuovi punto di interruzione | Microsoft Docs
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
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517465"
---
# <a name="toggle-breakpoint-command"></a>Comando Imposta/Rimuovi punto di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Attiva/Disattiva punto di interruzione comando](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command).  
  
  
Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Facoltativo. Se il testo viene specificato, la riga viene contrassegnata come punto di interruzione con nome. In caso contrario, la riga viene contrassegnata come punto di interruzione senza nome, analogamente a quanto accade quando si preme F9.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il punto di interruzione corrente viene impostato/rimosso.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



