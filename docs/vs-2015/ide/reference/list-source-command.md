---
title: Comando Elenca origine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: ff216ddd8943ea971669c6ebb1c7c0306b02160f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171977"
---
# <a name="list-source-command"></a>Comando Elenca origine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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



