---
title: Comando Elenca origine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672326"
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
 /Count: `number` facoltativo. Specifica il numero di righe da visualizzare.

 /Current. facoltativo. Visualizza la riga corrente.

 /File: `filename` facoltativo. Percorso del file da visualizzare. Se non viene specificato alcun nome file, il comando visualizza il codice sorgente per la riga dell'istruzione corrente.

 /Linea: `number` facoltativo. Visualizza un numero di riga specifico.

 /ShowLineNumbers: `yes|no` facoltativo. Specifica se visualizzare i numeri di riga.

## <a name="remarks"></a>Osservazioni

## <a name="example"></a>Esempio
 In questo esempio viene elencato il codice sorgente dalla riga 4 del file Form1.vb, con i numeri di riga visibili.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Vedere anche
 [Finestra di comando](../../ide/reference/command-window.md) di [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)
