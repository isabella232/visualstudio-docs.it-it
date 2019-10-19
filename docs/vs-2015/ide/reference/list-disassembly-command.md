---
title: Comando Elenca disassembly | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672733"
---
# <a name="list-disassembly-command"></a>Comando Elenca disassembly
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.

## <a name="syntax"></a>Sintassi

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Opzioni
 Ogni opzione può essere richiamata usando la forma completa o una forma breve.

 /Count: `number` [o]/c: `number` [o]/length: `number` [o]/l: `number` facoltativo. Numero di istruzioni da visualizzare. Il valore predefinito è 8.

 /endaddress: `expression` [o]/e: `expression` facoltativa. Indirizzo in corrispondenza del quale interrompere il disassembly.

 /codebytes: `yes`&#124; `no` [o]/bytes: `yes`&#124; `no` [o]/B: `yes`&#124; `no` facoltativo. Indica se visualizzare i byte di codice. Il valore predefinito è `no`.

 /Source: `yes`&#124; `no` [o]/s: `yes`&#124; `no` facoltativo. Indica se visualizzare il codice sorgente. Il valore predefinito è `no`.

 /SymbolNames: `yes`&#124; `no` [o]/names: `yes`&#124; `no` [o]/N: `yes`&#124; `no` facoltativo. Indica se visualizzare i nomi dei simboli. Il valore predefinito è `yes`.

 [opzione/linenumbers: `yes`&#124; `no`] Opzionale. Abilita la visualizzazione dei numeri di riga associati al codice sorgente. L'opzione /source deve avere un valore di `yes` per usare l'opzione /linenumbers.

## <a name="example"></a>Esempio

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Vedere anche
 [Elenco dei comandi di stack di chiamate](../../ide/reference/list-call-stack-command.md) [elenco dei](../../ide/reference/list-threads-command.md) [comandi comandi di Visual Studio comandi](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando](../../ide/find-command-box.md) [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
