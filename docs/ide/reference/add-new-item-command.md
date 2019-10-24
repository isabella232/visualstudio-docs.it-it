---
title: Comando Aggiungi nuovo elemento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 683a65ab0c25a5daeb002a4eb3106006655a1b00
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748816"
---
# <a name="add-new-item-command"></a>Comando Aggiungi nuovo elemento
Aggiunge un nuovo elemento, ad esempio un file con estensione htm, css o txt o una pagina con frame, alla soluzione corrente e lo apre.

## <a name="syntax"></a>Sintassi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>argomenti
`filename`\
Parametro facoltativo. Percorso e nome file dell'elemento da aggiungere alla soluzione.

## <a name="switches"></a>Opzioni
/t: `templatename`\
Parametro facoltativo. Specifica il tipo di file da creare. Se non viene specificato alcun modello, per impostazione predefinita viene creato un file di testo.

La sintassi dell'argomento /t:`templatename` riflette le informazioni riportate nella finestra di dialogo **Aggiungi nuovo elemento di soluzione**. È necessario immettere il nome completo della categoria e il tipo di file separati da una barra rovesciata (`\`) racchiudendo l'intera stringa tra virgolette.

Ad esempio, per creare un nuovo file di testo, per l'argomento /t:`templatename` è necessario immettere quanto segue.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
Parametro facoltativo. Il nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.

La sintassi dell'argomento `editorname` usa i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette.

Ad esempio, per aprire un foglio di stile nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Esempio
In questo esempio un nuovo elemento di soluzione, denominato MyHTMLpg, viene aggiunto alla soluzione corrente.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)