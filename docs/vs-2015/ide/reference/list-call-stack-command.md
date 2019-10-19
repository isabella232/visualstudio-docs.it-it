---
title: Comando Elenca stack di chiamate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657652"
---
# <a name="list-call-stack-command"></a>Comando Elenca stack di chiamate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza lo stack di chiamate corrente.

## <a name="syntax"></a>Sintassi

```
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

 /Count: `number` [o]/C: `number` facoltativa. Numero massimo di stack di chiamate da visualizzare. Il valore predefinito è illimitato.

 /ShowTypes: `yes`&#124; `no` [o]/t: `yes`&#124; `no` facoltativo. Specifica se visualizzare i tipi di parametro. Il valore predefinito è `yes`.

 /ShowNames: `yes`&#124; `no` [o]/n: `yes`&#124; `no` facoltativo. Specifica se visualizzare i nomi dei parametri. Il valore predefinito è `yes`.

 /ShowValues: `yes`&#124; `no` [o]/v: `yes`&#124; `no` facoltativo. Specifica se visualizzare i valori dei parametri. Il valore predefinito è `yes`.

 /ShowModule: `yes`&#124; `no` [o]/m: `yes`&#124; `no` facoltativo. Specifica se visualizzare il nome del modulo. Il valore predefinito è `yes`.

 /ShowLineOffset: `yes`&#124; `no` [or]/#: `yes`&#124; `no` facoltativo. Specifica se visualizzare l'offset di riga. Il valore predefinito è `no`.

 /ShowByteOffset: `yes`&#124; `no` [o]/b: `yes`&#124; `no` facoltativo. Specifica se visualizzare l'offset di byte. Il valore predefinito è `no`.

 /ShowLanguage: `yes`&#124; `no` [o]/l: `yes`&#124; `no` facoltativo. Specifica se visualizzare la lingua. Il valore predefinito è `no`.

 /IncludeCallsAcrossThreads: `yes`&#124; `no` [o]/i: `yes`&#124; `no` facoltativo. Specifica se includere le chiamate a o da altri thread. Il valore predefinito è `no`.

 /ShowExternalCode: `yes`&#124; `no` facoltativa. Specifica se visualizzare Just My Code per lo stack di chiamate. Se l'opzione Just My Code è disattivata, viene visualizzato tutto il codice non utente. Se l'opzione Just My Code è attivata, il codice non utente viene visualizzato come `[external]` nell'output dello stack di chiamate.

 Thread: `n` facoltativo. Consente di visualizzare lo stack di chiamate per il thread `n`. Se non viene specificato alcun thread, visualizza lo stack di chiamate per il thread corrente.

## <a name="remarks"></a>Osservazioni
 Le modifiche apportate a opzioni o argomenti si applicano alle chiamate future di questo comando. Se si emette Debug.ListCallStackby, viene visualizzato l'intero stack di chiamate. Se si specifica un indice, ad esempio,

```
Debug.ListCallStack 2
```

 lo stack frame corrente viene impostato su quel frame, in questo caso il secondo.

 È anche possibile scrivere questo comando usando il relativo alias predefinito, kb. Ad esempio, è possibile immettere

```
kb 2
```

 per impostare lo stack frame corrente sul secondo frame.

## <a name="example"></a>Esempio

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Vedere anche
 [Elenco comandi Disassembly comando](../../ide/reference/list-disassembly-command.md) [elenco thread](../../ide/reference/list-threads-command.md) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [trovare/comando casella](../../ide/find-command-box.md) di comando [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
