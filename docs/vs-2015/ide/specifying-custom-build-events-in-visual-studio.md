---
title: Specifica di eventi di compilazione personalizzati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d00c520f75869e6cf886074c482575f1170e923a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679521"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Specifica di eventi di compilazione personalizzati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si specifica un evento di compilazione personalizzato, sarà possibile eseguire automaticamente i comandi prima dell'avvio o dopo il completamento di una compilazione. Ad esempio, è possibile eseguire un file con estensione bat prima dell'avvio di una compilazione o copiare nuovi file in una cartella dopo il completamento della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.

 Per informazioni specifiche sul linguaggio di programmazione in uso, vedere gli argomenti seguenti:

- Visual Basic: [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- Visual C# e F#-consente[procedura: Specificare eventi di compilazione (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++: [Specifica di eventi di compilazione](https://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).

## <a name="syntax"></a>Sintassi
 Gli eventi di compilazione seguono la stessa sintassi dei comandi DOS, ma è possibile usare macro per creare con maggiore facilità gli eventi di compilazione. Per un elenco delle macro disponibili, vedere [Finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Per ottenere risultati ottimali, seguire questi suggerimenti di formattazione:

- Aggiungere un'istruzione `call` prima di tutti gli eventi di compilazione che eseguono file con estensione bat.

     Esempio: `call C:\MyFile.bat`

     Esempio: `call C:\MyFile.bat call C:\MyFile2.bat`

- Racchiudere tra virgolette i percorsi dei file.

     Esempio (per [!INCLUDE[win8](../includes/win8-md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Separare più comandi usando le interruzioni di riga.

- Includere i caratteri jolly, se necessario.

     Esempio: `for %I in (*.txt *.doc *.html) do copy %I c:\`*directory*`\`

    > [!NOTE]
    > `%I` nel codice sopra riportato deve essere `%%I` negli script batch.

## <a name="see-also"></a>Vedere anche
 [Compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md) [pre-compilazione/Post-compilazione eventi finestra di dialogo riga di comando](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md) [procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md)
