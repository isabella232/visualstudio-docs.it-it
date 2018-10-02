---
title: Comando Elenca origine | Microsoft Docs
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
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce57d39d609268e2570d588e6863eb1e8b8d3111
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527651"
---
# <a name="list-source-command"></a>Comando Elenca origine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [comando Elenca origine](https://docs.microsoft.com/visualstudio/ide/reference/list-source-command).  
  
  
Visualizza le righe del codice sorgente specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Opzioni  
 /Count:`number`  
 Facoltativo. Specifica il numero di righe da visualizzare.  
  
 /Current  
 Facoltativo. Visualizza la riga corrente.  
  
 /File:`filename`  
 Facoltativo. Percorso del file da visualizzare. Se non viene specificato alcun nome file, il comando visualizza il codice sorgente per la riga dell'istruzione corrente.  
  
 /Line:`number`  
 Facoltativo. Visualizza un numero di riga specifico.  
  
 /ShowLineNumbers:`yes|no`  
 Facoltativo. Specifica se visualizzare i numeri di riga.  
  
## <a name="remarks"></a>Note  
  
## <a name="example"></a>Esempio  
 In questo esempio viene elencato il codice sorgente dalla riga 4 del file Form1.vb, con i numeri di riga visibili.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md) (Finestra di comando)



