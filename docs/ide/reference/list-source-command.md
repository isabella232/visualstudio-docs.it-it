---
title: Comando Elenca origine
description: Informazioni sul comando List Source e su come visualizza le righe di codice sorgente specificate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 467abd21c80036b1b16edbb1b64ee818ca726e5e3218eb77d002408c49843e1c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387421"
---
# <a name="list-source-command"></a>Comando Elenca origine
Visualizza le righe del codice sorgente specificate.

## <a name="syntax"></a>Sintassi

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Commutatori
/Count:`number`

facoltativo. Specifica il numero di righe da visualizzare.

/Current

facoltativo. Visualizza la riga corrente.

/File:`filename`

facoltativo. Percorso del file da visualizzare. Se non viene specificato alcun nome file, il comando visualizza il codice sorgente per la riga dell'istruzione corrente.

/Line:`number`

facoltativo. Visualizza un numero di riga specifico.

/ShowLineNumbers:`yes|no`

facoltativo. Specifica se visualizzare i numeri di riga.

## <a name="example"></a>Esempio
In questo esempio viene elencato il codice sorgente dalla riga 4 del file Form1.vb, con i numeri di riga visibili.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)