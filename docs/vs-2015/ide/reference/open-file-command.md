---
title: Comando Apri file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671939"
---
# <a name="open-file-command"></a>Comando Apri file
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Apre un file esistente e consente di specificare un editor.

## <a name="syntax"></a>Sintassi

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argomenti
 `filename` Obbligatorio. Percorso completo o parziale e nome file del file da aprire. I percorsi contenenti spazi devo devono essere racchiusi tra virgolette.

## <a name="switches"></a>Opzioni
 /e:`editorname` Facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

 La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.

 Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Osservazioni
 Quando si immette un percorso, il completamento automatico tenta di individuare il percorso e il nome file corretti.

## <a name="example"></a>Esempio
 In questo esempio viene aperto il file di stile "Test1.css" nell'editor del codice sorgente.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vedere anche
 [Finestra di comando](../../ide/reference/command-window.md) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) finestra di dialogo [immediata finestra](../../ide/reference/immediate-window.md) [Trova/comando](../../ide/find-command-box.md) [Visual Studio alias del comando](../../ide/reference/visual-studio-command-aliases.md)
