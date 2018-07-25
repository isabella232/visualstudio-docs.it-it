---
title: Comando Apri file
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4be55cb2108b24c7a8f912844b719e6aa3135a06
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924000"
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

## <a name="switches"></a>Opzioni

/e:`editorname`

Facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.

Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Note

Quando si immette un percorso, il completamento automatico tenta di individuare il percorso e il nome file corretti.

## <a name="example"></a>Esempio

In questo esempio viene aperto il file di stile "Test1.css" nell'editor del codice sorgente.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Finestra di controllo immediato](../../ide/reference/immediate-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)