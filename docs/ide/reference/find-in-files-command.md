---
title: Comando Cerca nei file
description: Informazioni sul comando Trova e su come cerca i file usando alcune delle opzioni disponibili nella scheda Trova nei file della finestra Trova e sostituisci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4886cd6d62fc35cccb9a7a7df1b70c1006e135a678abe1f25bf7dfda5bbc948f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429446"
---
# <a name="find-in-files-command"></a>Comando Cerca nei file
Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.

## <a name="syntax"></a>Sintassi

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argomenti

`findwhat`\
Obbligatorio. Testo da cercare.

## <a name="switches"></a>Commutatori
/case o /c\
facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.

/ext: `extensions`\
facoltativo. Specifica l'estensione dei file nei quali eseguire la ricerca. Se non è specificato e in precedenza è stata immessa un'estensione, viene usata tale estensione.

/lookin: `searchpath`\
facoltativo. Directory in cui eseguire la ricerca. Se il percorso contiene spazi, racchiudere l'intero percorso tra virgolette.

/names o /n\
facoltativo. Visualizza l'elenco dei nomi file che contengono corrispondenze.

/options o /t\
facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.

/regex o /r\
facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).

/reset o /e\
facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.

/stop\
facoltativo. Se è in corso un'operazione di ricerca, la interrompe. Quando viene specificato `/stop` la ricerca ignora tutti gli altri argomenti. Ad esempio, per interrompere la ricerca corrente immettere quanto segue:

```cmd
>Edit.FindinFiles /stop
```

/sub o /s\
facoltativo. Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento /lookin:`searchpath`.

/text2 o /2\
facoltativo. Visualizza i risultati della ricerca nella finestra Risultati ricerca 2.

/wild o /l\
facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.

/word o /w\
facoltativo. Cerca solo parole intere.

## <a name="example"></a>Esempio
Nell'esempio riportato di seguito viene cercato btnCancel in tutti i file CLS presenti nella cartella "My Visual Studio Projects" e le informazioni sulle corrispondenze trovate vengono visualizzate nella finestra Risultati ricerca 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Vedi anche

- [Cerca nei file](../../ide/find-in-files.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
