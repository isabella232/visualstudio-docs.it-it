---
title: Comando Elenca registri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 942ab10a1d660ea5e33ca2cb679e4655bd6b3fbc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959965"
---
# <a name="list-registers-command"></a>Comando Elenca registri
Consente di visualizzare il valore dei registri selezionati e di modificare l'elenco dei registri da visualizzare.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Opzioni
 /Display [{`register`&#124;`registerGroup`}...]

 Consente di visualizzare i valori dell'oggetto `register` o `registerGroup` specificato. Se non è stato specificato alcun oggetto `register` o `registerGroup`, viene visualizzato l'elenco predefinito dei registri. Se non viene specificata alcuna opzione, il comportamento è lo stesso. Ad esempio:

 `Debug.ListRegisters /Display eax`

 equivale a

 `Debug.ListRegisters eax`

 /List

 Consente di visualizzare tutti i gruppi di registri nell'elenco.

 /Watch [{`register`&#124;`registerGroup`}...]

 Aggiunge uno o più valori `register` o `registerGroup` all'elenco.

 /Unwatch [{`register`&#124;`registerGroup`}...]

 Rimuove uno o più valori `register` o `registerGroup` dall'elenco.

## <a name="remarks"></a>Note
 L'alias `r` può essere usato al posto di `Debug.ListRegisters`.

## <a name="example"></a>Esempio
 In questo esempio viene usato l'alias di `Debug.ListRegisters` `r` per visualizzare i valori del gruppo di registri `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Informazioni di base sul debug: Finestra Registri](../../debugger/debugging-basics-registers-window.md)
- [Procedura: Usare la finestra Registri](../../debugger/how-to-use-the-registers-window.md)