---
title: Comando Aggiungi elemento esistente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f636c2a0eb2cfdcebf383fdc7eea70f72cb90e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670230"
---
# <a name="add-existing-item-command"></a>Comando Aggiungi elemento esistente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aggiunge un file esistente alla soluzione corrente e lo apre.

## <a name="syntax"></a>Sintassi

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argomenti
 `filename` Obbligatorio. Percorso completo e nome del file con estensione dell'elemento da aggiungere alla soluzione corrente. Se il percorso o il nome del file contiene spazi, racchiudere l'intero percorso tra virgolette.

## <a name="switches"></a>Opzioni
 /e: `editorname` Facoltativo. Nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

 La sintassi dell'argomento `editorname` usa i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette. Ad esempio, per aprire un foglio di stile nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Osservazioni
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.

## <a name="example"></a>Esempio
 In questo esempio viene aggiunto il file Form1.frm alla soluzione corrente.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
