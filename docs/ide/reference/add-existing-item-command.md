---
title: Comando Aggiungi elemento esistente
description: Informazioni sul comando Aggiungi elemento esistente e su come aggiunge un file esistente a una soluzione corrente e lo apre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59d1e032150035258df4b1cc88253cefc555d826
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871028"
---
# <a name="add-existing-item-command"></a>Comando Aggiungi elemento esistente
Aggiunge un file esistente alla soluzione corrente e lo apre.

## <a name="syntax"></a>Sintassi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argomenti
`filename`\
Obbligatorio. Percorso completo e nome del file con estensione dell'elemento da aggiungere alla soluzione corrente. Se il percorso o il nome del file contiene spazi, racchiudere l'intero percorso tra virgolette.

## <a name="switches"></a>Commutatori
/e: `editorname`\
facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento `editorname` usa i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette. Ad esempio, per aprire un foglio di stile nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Commenti
Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
In questo esempio viene aggiunto il file Form1.frm alla soluzione corrente.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
