---
title: Comando Elenca disassembly
description: Informazioni sul comando list Disassembly e sul modo in cui avvia il processo di debug e consente di specificare come vengono gestiti gli errori.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15e9016551b178b0a29656e615d029ddaf0ca279
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305339"
---
# <a name="list-disassembly-command"></a>Comando Elenca disassembly
Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Commutatori
Ogni opzione può essere richiamata usando la forma completa o una forma breve.

/count: `number` [or] /c: `number` [or] /length: `number` [or] /l: `number`

facoltativo. Numero di istruzioni da visualizzare. Il valore predefinito è 8.

/endaddress: `expression` [or] /e: `expression`

facoltativo. Indirizzo in corrispondenza del quale interrompere il disassembly.

/codebytes:`yes`&#124;`no` [or] /bytes:`yes`&#124;`no` [or] /b:`yes`&#124;`no`

facoltativo. Indica se visualizzare i byte di codice. Il valore predefinito è `no`.

/source:`yes`&#124;`no` [or] /s:`yes`&#124;`no`

facoltativo. Indica se visualizzare il codice sorgente. Il valore predefinito è `no`.

/symbolnames:`yes`&#124;`no` [or] /names:`yes`&#124;`no` [or] /n:`yes`&#124;`no`

facoltativo. Indica se visualizzare i nomi dei simboli. Il valore predefinito è `yes`.

 [/linenumbers:`yes`&#124;`no`]

facoltativo. Abilita la visualizzazione dei numeri di riga associati al codice sorgente. L'opzione /source deve avere un valore di `yes` per usare l'opzione /linenumbers.

## <a name="example"></a>Esempio

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando list Threads](../../ide/reference/list-threads-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)