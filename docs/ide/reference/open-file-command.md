---
title: Comando Apri file
description: Informazioni sul comando Apri file e su come apre un file esistente e consente di specificare un editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: aa31ee8ce28b29f81066e12f80aa0c73fccb8731
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117319"
---
# <a name="open-file-command"></a>Comando Apri file

Apre un file esistente e consente di specificare un editor.

## <a name="syntax"></a>Sintassi

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argomenti

`filename`

Obbligatorio. Percorso completo o parziale e nome file del file da aprire. I percorsi contenenti spazi devo devono essere racchiusi tra virgolette.

## <a name="switches"></a>Commutatori

/e:`editorname`

facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.

Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Commenti

Quando si immette un percorso, il completamento automatico tenta di individuare il percorso e il nome file corretti.

## <a name="example"></a>Esempio

In questo esempio viene aperto il file di stile "Test1.css" nell'editor del codice sorgente.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vedi anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Controllo immediato (finestra)](../../ide/reference/immediate-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
