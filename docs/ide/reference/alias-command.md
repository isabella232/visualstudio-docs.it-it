---
title: Comando Alias
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fdcc816510642c7800b6fbeacfa3fcdeff5e0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748791"
---
# <a name="alias-command"></a>Comando Alias
Crea un nuovo alias per un comando completo, un comando completo con i relativi argomenti o un altro alias.

> [!TIP]
> Digitando `>alias` senza alcun argomento verrà visualizzato l'elenco corrente di alias e le relative definizioni.

## <a name="syntax"></a>Sintassi

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>argomenti
`aliasname`\
Parametro facoltativo. Nome del nuovo alias. Se per `aliasname` non viene specificato alcun valore, verrà visualizzato un elenco degli alias correnti e le relative definizioni.

`aliasstring`\
Parametro facoltativo. Nome del comando completo o alias esistente e i parametri da creare come alias. Se per `aliasstring` non viene specificato alcun valore, verranno visualizzati il nome di alias e la stringa di alias per l'alias specificato.

## <a name="switches"></a>Opzioni
/delete o /del o /d\
Parametro facoltativo. Elimina l'alias specificato rimuovendolo dal completamento automatico.

/reset\
Parametro facoltativo. Ripristina le impostazioni originali dell'elenco di alias predefiniti, ovvero ripristina tutti gli alias predefiniti e rimuove tutti gli alias definiti dall'utente.

## <a name="remarks"></a>Note
Poiché rappresentano i comandi, gli alias devono essere posizionati all'inizio della riga di comando.

Quando si esegue questo comando, le opzioni devono essere incluse subito dopo il comando, non dopo gli alias. In caso contrario, l'opzione verrà considerata parte della stringa di alias.

L'opzione `/reset` chiede una conferma prima del ripristino degli alias. Non esiste una forma breve di `/reset`.

## <a name="examples"></a>Esempi
In questo esempio viene creato un nuovo alias, `upper`, per il comando completo Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

In questo esempio l'alias `upper` viene eliminato.

```cmd
>Tools.alias /delete upper
```

In questo esempio viene visualizzato un elenco di tutti gli alias correnti e le relative definizioni.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)