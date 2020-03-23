---
title: Specificare eventi di compilazione personalizzati
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda60ffb97ecb44bd4a881cb42e4d9199cc958b8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115337"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Specificare gli eventi di compilazione personalizzati in Visual Studio

Se si specifica un evento di compilazione personalizzato, sarà possibile eseguire automaticamente i comandi prima dell'avvio o dopo il completamento di una compilazione. Ad esempio, è possibile eseguire un file *bat* prima dell'avvio di una compilazione o copiare nuovi file in una cartella al termine della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.

Per informazioni specifiche sul linguaggio di programmazione in uso, vedere gli argomenti seguenti:

- Visual Basic--[Procedura: specificare gli eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- In C' e F:[procedura: specificare gli eventi di compilazione (C)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++: [Specificare gli eventi di compilazione](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Sintassi

Gli eventi di compilazione seguono la stessa sintassi dei comandi DOS, ma è possibile usare macro per creare con maggiore facilità gli eventi di compilazione. Per un elenco delle macro disponibili, vedere Finestra di dialogo Riga di [comando Eventi pre-compilazione/evento post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Per ottenere risultati ottimali, seguire questi suggerimenti di formattazione:

- Aggiungere `call` un'istruzione prima di tutti gli eventi di compilazione che eseguono file *bat.*

   Esempio: `call C:\MyFile.bat`

   Esempio: `call C:\MyFile.bat call C:\MyFile2.bat`

- Racchiudere tra virgolette i percorsi dei file.

   Esempio (per [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Separare più comandi usando le interruzioni di riga.

- Includere i caratteri jolly, se necessario.

   Esempio: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I` nel codice sopra riportato deve essere `%%I` negli script batch.

## <a name="see-also"></a>Vedere anche

- [Compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md)
- [Finestra di dialogo Riga di comando Eventi pre-compilazione/evento post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Caratteri speciali MSBuild](../msbuild/msbuild-special-characters.md)
- [Procedura dettagliata: compilare un'applicazioneWalkthrough: Build an application](../ide/walkthrough-building-an-application.md)
