---
title: Comando Nuovo file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671954"
---
# <a name="new-file-command"></a>Comando Nuovo file
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea un nuovo file e lo apre. Il file viene visualizzato nella cartella File esterni.

## <a name="syntax"></a>Sintassi

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argomenti
 `filename` Facoltativo. Nome del file. Se non viene specificato alcun nome, viene indicato un nome predefinito. Se non viene elencato alcun nome di modello, viene creato un file di testo.

## <a name="switches"></a>Commutatori
 /t:`templatename` Facoltativo. Specifica il tipo di file da creare.

 La sintassi dell'argomento /t:`templatename` riflette le informazioni riportate nella finestra di dialogo Nuovo file. Immettere il nome categoria seguito da una barra rovesciata (`\`) e il nome del modello e racchiudere l'intera stringa tra virgolette.

 Ad esempio, per creare un nuovo file di origine [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], per l'argomento /t:`templatename` è necessario immettere quanto segue.

```
/t:"Visual C++\C++ File (.cpp)"
```

 L'esempio precedente indica che il modello di file di C++ è incluso nella categoria Visual C++ nella finestra di dialogo **Nuovo file**.

 /e:`editorname` Facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

 La sintassi dell'argomento /e:`editorname` usa i nomi degli editor così come visualizzati nella finestra di dialogo Apri con, racchiusi tra virgolette.

 Ad esempio, per aprire un file nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Esempio
 In questo esempio viene creata una nuova pagina Web "test1.htm" e aperta nell'editor del codice sorgente.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Vedere anche
 [Finestra di comando](../../ide/reference/command-window.md) [comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) finestra di dialogo [immediata finestra](../../ide/reference/immediate-window.md) [Trova/comando](../../ide/find-command-box.md) [Visual Studio alias del comando](../../ide/reference/visual-studio-command-aliases.md)
