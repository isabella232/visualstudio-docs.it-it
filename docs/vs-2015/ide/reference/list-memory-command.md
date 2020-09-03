---
title: Comando Elenca memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672754"
---
# <a name="list-memory-command"></a>Comando Elenca memoria
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza il contenuto dell'intervallo di memoria specificato.

## <a name="syntax"></a>Sintassi

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Argomenti
 `expression` Facoltativo. L'indirizzo di memoria da cui iniziare la visualizzazione della memoria.

## <a name="switches"></a>Commutatori
 /ANSI&#124;Unicode facoltativo. Visualizza la memoria come caratteri corrispondenti ai byte di memoria, ANSI o Unicode.

 /Count: `number` facoltativo. Determina il numero di byte di memoria da visualizzare, a partire da `expression`.

 /Format: `formattype` facoltativo. Tipo di formato per la visualizzazione di informazioni sulla memoria nella finestra **Memoria**; può essere OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bit) o Double (64 bit). Se viene usato il formato OneByte, `/Unicode` non è disponibile.

 /Hex&#124;firmato&#124;facoltativo senza segno. Specifica il formato per la visualizzazione dei numeri: con segno, senza segno o esadecimale.

## <a name="remarks"></a>Osservazioni
 Invece di scrivere un comando **Debug.ListMemory** completo con tutte le opzioni, è possibile richiamare il comando tramite alias predefiniti con alcune opzioni preimpostate su valori specificati. Ad esempio, anziché immettere:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 è possibile scrivere:

```
>df /Count:30 /Unicode
```

 Di seguito viene riportato un elenco degli alias disponibili per il comando **Debug.ListMemory**:

|Alias|Comandi e opzioni|
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**DB**|Debug.ListMemory /Format:OneByte|
|**DC**|Debug.ListMemory /Format:FourBytes /Ansi|
|**gg**|Debug.ListMemory /Format:FourBytes|
|**DF**|Debug.ListMemory /Format:Float|
|**DQ**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Esempio

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Vedere anche
 [Elenco dei comandi di stack di chiamate](../../ide/reference/list-call-stack-command.md) [elenco dei](../../ide/reference/list-threads-command.md) [comandi comandi di Visual Studio comandi](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando](../../ide/find-command-box.md) [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
