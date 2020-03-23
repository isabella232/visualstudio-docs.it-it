---
title: Comando Elenca disassembly
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747927"
---
# <a name="list-disassembly-command"></a>Comando Elenca disassembly
Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Switch
Ogni opzione può essere richiamata usando la forma completa o una forma breve.

/count: `number` [or] /c: `number` [or] /length: `number` [or] /l: `number`

Facoltativa. Numero di istruzioni da visualizzare. Il valore predefinito è 8.

/endaddress: `expression` [or] /e: `expression`

Facoltativa. Indirizzo in corrispondenza del quale interrompere il disassembly.

/codebytes:`yes`&#124;`no` [or] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`

Facoltativa. Indica se visualizzare i byte di codice. Il valore predefinito è `no`.

/source:`yes`&#124;`no` [or] /s:`yes`&#124;`no`

Facoltativa. Indica se visualizzare il codice sorgente. Il valore predefinito è `no`.

/symbolnames:`yes`&#124;`no` [or] /names:`yes`&#124;`no` [or] /n:`yes`&#124;`no`

Facoltativa. Indica se visualizzare i nomi dei simboli. Il valore predefinito è `yes`.

 [/linenumbers:`yes`&#124;`no`]

Facoltativa. Abilita la visualizzazione dei numeri di riga associati al codice sorgente. L'opzione /source deve avere un valore di `yes` per usare l'opzione /linenumbers.

## <a name="example"></a>Esempio

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando Elenca thread](../../ide/reference/list-threads-command.md)
- [Visual Studio Commands](../../ide/reference/visual-studio-commands.md) (Comandi di Visual Studio)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)