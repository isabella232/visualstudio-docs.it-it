---
title: Comando Elenca stack di chiamate
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e04bb46d167478b85f4b6f8b4d6df903bd46e8b7
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704616"
---
# <a name="list-call-stack-command"></a>Comando Elenca stack di chiamate
Visualizza lo stack di chiamate corrente.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Argomenti
 `index` Facoltativo. Imposta lo stack frame corrente e non visualizza alcun output.

## <a name="switches"></a>Opzioni
 Ogni opzione può essere richiamata usando la forma completa o una forma breve.

 /Count:`number` [o] /C:`number`

 Facoltativo. Numero massimo di stack di chiamate da visualizzare. Il valore predefinito è illimitato.

 /ShowTypes:`yes`&#124;`no` [o] /T:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare i tipi di parametro. Il valore predefinito è `yes`.

 /ShowNames:`yes`&#124;`no` [o] /N:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare i nomi dei parametri. Il valore predefinito è `yes`.

 /ShowValues:`yes`&#124;`no` [o] /V:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare i valori dei parametri. Il valore predefinito è `yes`.

 /ShowModule:`yes`&#124;`no` [o] /M:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare il nome del modulo. Il valore predefinito è `yes`.

 /ShowLineOffset:`yes`&#124;`no` [o] /#:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare l'offset di riga. Il valore predefinito è `no`.

 /ShowByteOffset:`yes`&#124;`no` [o] /B:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare l'offset di byte. Il valore predefinito è `no`.

 /ShowLanguage:`yes`&#124;`no` [o] /L:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare la lingua. Il valore predefinito è `no`.

 /IncludeCallsAcrossThreads:`yes`&#124;`no` [o] /I:`yes`&#124;`no`

 Facoltativo. Specifica se includere le chiamate a o da altri thread. Il valore predefinito è `no`.

 /ShowExternalCode:`yes`&#124;`no`

 Facoltativo. Specifica se visualizzare Just My Code per lo stack di chiamate. Se l'opzione Just My Code è disattivata, viene visualizzato tutto il codice non utente. Se l'opzione Just My Code è attivata, il codice non utente viene visualizzato come `[external]` nell'output dello stack di chiamate.

 Thread:`n`

 Facoltativo. Consente di visualizzare lo stack di chiamate per il thread `n`. Se non viene specificato alcun thread, visualizza lo stack di chiamate per il thread corrente.

## <a name="remarks"></a>Note
 Le modifiche apportate a opzioni o argomenti si applicano alle chiamate future di questo comando. Se si emette Debug.ListCallStackby, viene visualizzato l'intero stack di chiamate. Se si specifica un indice, ad esempio,

```cmd
Debug.ListCallStack 2
```

 lo stack frame corrente viene impostato su quel frame, in questo caso il secondo.

 È anche possibile scrivere questo comando usando il relativo alias predefinito, kb. Ad esempio, è possibile immettere

```cmd
kb 2
```

 per impostare lo stack frame corrente sul secondo frame.

## <a name="example"></a>Esempio

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca disassembly](../../ide/reference/list-disassembly-command.md)
- [Comando Elenca thread](../../ide/reference/list-threads-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)