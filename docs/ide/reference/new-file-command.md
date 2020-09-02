---
title: Comando Nuovo file
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe8a99ee59a347fdcb7cff601b75139760630f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595956"
---
# <a name="new-file-command"></a>Comando Nuovo file
Crea un nuovo file e lo apre. Il file viene visualizzato nella cartella File esterni.

## <a name="syntax"></a>Sintassi

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argomenti
`filename`

facoltativo. Nome del file. Se non viene specificato alcun nome, viene indicato un nome predefinito. Se non viene elencato alcun nome di modello, viene creato un file di testo.

## <a name="switches"></a>Commutatori
/t:`templatename`\
facoltativo. Specifica il tipo di file da creare.

La sintassi dell'argomento /t:`templatename` riflette le informazioni riportate nella finestra di dialogo Nuovo file. Immettere il nome categoria seguito da una barra rovesciata (`\`) e il nome del modello e racchiudere l'intera stringa tra virgolette.

Ad esempio, per creare un nuovo file di origine [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], per l'argomento /t:`templatename` è necessario immettere quanto segue.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

L'esempio precedente indica che il modello di file di C++ è incluso nella categoria Visual C++ nella finestra di dialogo **Nuovo file**.

/e:`editorname`\
facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.

Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Esempio
In questo esempio viene creata una nuova pagina Web "test1.htm" e la pagina viene aperta nell'editor del codice sorgente.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Finestra di controllo immediato](../../ide/reference/immediate-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
