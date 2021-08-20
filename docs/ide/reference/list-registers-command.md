---
title: Comando Elenca registri
description: Informazioni sul comando List Registers e su come visualizza il valore dei registri selezionati e consente di modificare l'elenco di registri da visualizzare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7bf6d9526e61327b1ff582a74c1624f1bfd7b8c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151431"
---
# <a name="list-registers-command"></a>Comando Elenca registri
Consente di visualizzare il valore dei registri selezionati e di modificare l'elenco dei registri da visualizzare.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Commutatori
/Display [{`register`&#124;`registerGroup`}...]

Consente di visualizzare i valori dell'oggetto `register` o `registerGroup` specificato. Se non è stato specificato alcun oggetto `register` o `registerGroup`, viene visualizzato l'elenco predefinito dei registri. Se non viene specificata alcuna opzione, il comportamento è lo stesso. Esempio:

`Debug.ListRegisters /Display eax`

equivale a

`Debug.ListRegisters eax`

/List

Consente di visualizzare tutti i gruppi di registri nell'elenco.

/Watch [{`register`&#124;`registerGroup`}...]

Aggiunge uno o più valori `register` o `registerGroup` all'elenco.

/Unwatch [{`register`&#124;`registerGroup`}...]

Rimuove uno o più valori `register` o `registerGroup` dall'elenco.

## <a name="remarks"></a>Commenti
L'alias `r` può essere usato al posto di `Debug.ListRegisters`.

## <a name="example"></a>Esempio
In questo esempio viene usato l'alias di `Debug.ListRegisters``r` per visualizzare i valori del gruppo di registri `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Nozioni fondamentali di debug: finestra Registri](../../debugger/debugging-basics-registers-window.md)
- [Procedura: utilizzare la finestra Registri](../../debugger/how-to-use-the-registers-window.md)
