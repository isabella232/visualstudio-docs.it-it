---
title: Comando Aggiungi elemento esistente
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89910a9504f587f97b0555f7f0d5ef7257ab4ae4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748833"
---
# <a name="add-existing-item-command"></a>Comando Aggiungi elemento esistente
Aggiunge un file esistente alla soluzione corrente e lo apre.

## <a name="syntax"></a>Sintassi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>argomenti
`filename`\
Obbligatorio. Percorso completo e nome del file con estensione dell'elemento da aggiungere alla soluzione corrente. Se il percorso o il nome del file contiene spazi, racchiudere l'intero percorso tra virgolette.

## <a name="switches"></a>Opzioni
/e: `editorname`\
Parametro facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento `editorname` usa i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette. Ad esempio, per aprire un foglio di stile nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Note
Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
In questo esempio viene aggiunto il file Form1.frm alla soluzione corrente.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)