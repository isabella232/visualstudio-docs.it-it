---
title: Comando Nuovo file
description: Informazioni sul comando Nuovo file e su come crea un nuovo file e lo apre.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4cb9e82ea6f44ddeb0e16ed8e70eed92612c0c07
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101037"
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

## <a name="see-also"></a>Vedi anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Finestra di controllo immediato](../../ide/reference/immediate-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
