---
title: Comando Elenca memoria
description: Informazioni sul comando Elenca memoria e su come visualizza il contenuto dell'intervallo di memoria specificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fe86f12ffba2d61783bd858f207f00803952fe83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085858"
---
# <a name="list-memory-command"></a>Comando Elenca memoria
Visualizza il contenuto dell'intervallo di memoria specificato.

## <a name="syntax"></a>Sintassi

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argomenti
`expression`

facoltativo. L'indirizzo di memoria da cui iniziare la visualizzazione della memoria.

## <a name="switches"></a>Commutatori
/ANSI&#124;Unicode

facoltativo. Visualizza la memoria come caratteri corrispondenti ai byte di memoria, ANSI o Unicode.

/Count:`number`

facoltativo. Determina il numero di byte di memoria da visualizzare, a partire da `expression`.

/Format:`formattype`

facoltativo. Tipo di formato per la visualizzazione di informazioni sulla memoria nella finestra **Memoria**; può essere OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bit) o Double (64 bit). Se viene usato il formato OneByte, `/Unicode` non è disponibile.

/Hex&#124;Signed&#124;Unsigned

facoltativo. Specifica il formato per la visualizzazione dei numeri: con segno, senza segno o esadecimale.

## <a name="remarks"></a>Commenti
Invece di scrivere un comando **Debug.ListMemory** completo con tutte le opzioni, è possibile richiamare il comando tramite alias predefiniti con alcune opzioni preimpostate su valori specificati. Ad esempio, anziché immettere:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

è possibile scrivere:

```cmd
>df /Count:30 /Unicode
```

Di seguito viene riportato un elenco degli alias disponibili per il comando **Debug.ListMemory**:

|Alias|Comandi e opzioni|
|-----------| - |
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**Db**|Debug.ListMemory /Format:OneByte|
|**Dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**Df**|Debug.ListMemory /Format:Float|
|**Dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Esempio

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando Elenca thread](../../ide/reference/list-threads-command.md)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
