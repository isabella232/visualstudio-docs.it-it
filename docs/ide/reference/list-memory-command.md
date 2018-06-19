---
title: Comando Elenca memoria
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3ce3aee4a7a498600da4eb0c99210c9c20d00f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703419"
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

 Facoltativo. L'indirizzo di memoria da cui iniziare la visualizzazione della memoria.

## <a name="switches"></a>Opzioni
 /ANSI&#124;Unicode

 Facoltativo. Visualizza la memoria come caratteri corrispondenti ai byte di memoria, ANSI o Unicode.

 /Count:`number`

 Facoltativo. Determina il numero di byte di memoria da visualizzare, a partire da `expression`.

 /Format:`formattype`

 Facoltativo. Tipo di formato per la visualizzazione di informazioni sulla memoria nella finestra **Memoria**; può essere OneByte, TwoBytes, FourBytes, EightBytes, Float (32 bit) o Double (64 bit). Se viene usato il formato OneByte, `/Unicode` non è disponibile.

 /Hex&#124;Signed&#124;Unsigned

 Facoltativo. Specifica il formato per la visualizzazione dei numeri: con segno, senza segno o esadecimale.

## <a name="remarks"></a>Note
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
|-----------|--------------------------|
|**d**|Debug.ListMemory|
|**da**|Debug.ListMemory /Ansi|
|**db**|Debug.ListMemory /Format:OneByte|
|**dc**|Debug.ListMemory /Format:FourBytes /Ansi|
|**dd**|Debug.ListMemory /Format:FourBytes|
|**df**|Debug.ListMemory /Format:Float|
|**dq**|Debug.ListMemory /Format:EightBytes|
|**du**|Debug.ListMemory /Unicode|

## <a name="example"></a>Esempio

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Vedere anche

- [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)
- [Comando Elenca thread](../../ide/reference/list-threads-command.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)