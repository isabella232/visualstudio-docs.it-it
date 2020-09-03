---
title: Comando Elenca memoria
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c500b1b516c2b1ab1bc66b7970fccc4ec7a85baa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568711"
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

## <a name="remarks"></a>Osservazioni
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
|**DB**|Debug.ListMemory /Format:OneByte|
|**DC**|Debug.ListMemory /Format:FourBytes /Ansi|
|**gg**|Debug.ListMemory /Format:FourBytes|
|**DF**|Debug.ListMemory /Format:Float|
|**DQ**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Esempio

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando list Threads](../../ide/reference/list-threads-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
