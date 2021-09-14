---
title: Comando Elenca disassembly
description: Informazioni sul comando List Disassembly e su come inizia il processo di debug e consente di specificare come vengono gestiti gli errori.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f41021b3b0d8c4dd0d0d688573bdc2e5c37da8f6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628740"
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
- [Comando Elenca thread](../../ide/reference/list-threads-command.md)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)