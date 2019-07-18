---
title: Comando Imposta/Rimuovi punto di interruzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 5a57f02a7c1b9845f4248daf2282b6f285f95489
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193368"
---
# <a name="toggle-breakpoint-command"></a>Comando Imposta/Rimuovi punto di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 facoltativo. Se il testo viene specificato, la riga viene contrassegnata come punto di interruzione con nome. In caso contrario, la riga viene contrassegnata come punto di interruzione senza nome, analogamente a quanto accade quando si preme F9.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il punto di interruzione corrente viene impostato/rimosso.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
