---
title: Comando Alias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651684"
---
# <a name="alias-command"></a>Comando Alias
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea un nuovo alias per un comando completo, un comando completo con i relativi argomenti o un altro alias.

> [!TIP]
> Digitando `>alias` senza alcun argomento verrà visualizzato l'elenco corrente di alias e le relative definizioni.

## <a name="syntax"></a>Sintassi

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argomenti
 `aliasname` Facoltativo. Nome del nuovo alias. Se per `aliasname` non viene specificato alcun valore, verrà visualizzato un elenco degli alias correnti e le relative definizioni.

 `aliasstring` Facoltativo. Nome del comando completo o alias esistente e i parametri da creare come alias. Se per `aliasstring` non viene specificato alcun valore, verranno visualizzati il nome di alias e la stringa di alias per l'alias specificato.

## <a name="switches"></a>Switch
 /delete o /del o /d Facoltativo. Elimina l'alias specificato rimuovendolo dal completamento automatico.

 /reimpostare Facoltativo. Ripristina le impostazioni originali dell'elenco di alias predefiniti, ovvero ripristina tutti gli alias predefiniti e rimuove tutti gli alias definiti dall'utente.

## <a name="remarks"></a>Osservazioni
 Poiché rappresentano i comandi, gli alias devono essere posizionati all'inizio della riga di comando.

 Quando si esegue questo comando, le opzioni devono essere incluse subito dopo il comando, non dopo gli alias. In caso contrario, l'opzione verrà considerata parte della stringa di alias.

 L'opzione `/reset` chiede una conferma prima del ripristino degli alias. Non esiste una forma breve di `/reset`.

## <a name="examples"></a>Esempi
 In questo esempio viene creato un nuovo alias, `upper`, per il comando completo Edit.MakeUpperCase.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 In questo esempio l'alias `upper` viene eliminato.

```
>Tools.alias /delete upper
```

 In questo esempio viene visualizzato un elenco di tutti gli alias correnti e le relative definizioni.

```
>Tools.Alias
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
