---
title: Comando Shell
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 502bb7b1ab6236fd88c7c6dbc789737e50686d89
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747748"
---
# <a name="shell-command"></a>Comando Shell
Avvia programmi eseguibili da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintassi

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>argomenti
`path`

Obbligatorio. Percorso e nome del file da eseguire o del documento da aprire. È necessario specificare un percorso completo se il file specificato non si trova in una delle directory incluse nella variabile di ambiente PATH.

`args`

Parametro facoltativo. Argomenti da passare al programma richiamato.

## <a name="switches"></a>Opzioni
/commandwindow [oppure] /command [oppure] /c [oppure] /cmd

Parametro facoltativo. Specifica che l'output per il file eseguibile verrà visualizzato nella finestra di **comando**.

/dir:`folder` [oppure] /d: `folder`

Parametro facoltativo. Specifica la cartella di lavoro da impostare all'esecuzione del programma.

/outputwindow [oppure] /output [oppure] /out [oppure] /o

Parametro facoltativo. Specifica che l'output per il file eseguibile verrà visualizzato nella finestra di **output**.

## <a name="remarks"></a>Note
Le opzioni /dir /o /c devono essere specificate immediatamente dopo `Tools.Shell`. Tutto ciò che viene specificato dopo il nome del file eseguibile viene passato all'eseguibile come argomento della riga di comando.

È possibile usare l'alias predefinito `Shell` invece di `Tools.Shell`.

> [!CAUTION]
> Se l'argomento `path` include sia il percorso della directory sia il nome del file, è consigliabile racchiudere l'intero percorso tra virgolette doppie adiacenti ("""), come nell'esempio seguente:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Ogni gruppo di tre virgolette doppie (""") viene interpretato dal processore `Shell` come un'unica virgoletta doppia. Nell'esempio precedente, pertanto, al comando `Shell` viene passata la stringa di percorso seguente:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Se la stringa di percorso non viene racchiusa tra virgolette doppie adiacenti ("""), Windows userà solo la porzione di stringa che precede il primo spazio. Se ad esempio la stringa di percorso usata nell'esempio precedente non fosse racchiusa tra virgolette in modo corretto, Windows cercherebbe un file denominato "Program" nella directory radice C:\. Qualora un file eseguibile C:\Program.exe fosse disponibile, anche se si trattasse di un file installato tramite una manomissione non autorizzata, Windows tenterebbe di eseguire quel programma anziché il programma desiderato "C:\Programmi\NomeFile.exe".

## <a name="example"></a>Esempio
Il comando seguente usa xcopy.exe per copiare il file `MyText.txt` nella cartella `Text`. L'output di xcopy.exe viene visualizzato nella **finestra di comando** e nella **finestra di output**.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Output (finestra)](../../ide/reference/output-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)