---
title: Comando Elenca origine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dcecdaa206964e6c8a5aebcadc958fe2c1ee1e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946856"
---
# <a name="list-source-command"></a>Comando Elenca origine
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

## <a name="example"></a>Esempio
 In questo esempio viene elencato il codice sorgente dalla riga 4 del file Form1.vb, con i numeri di riga visibili.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)