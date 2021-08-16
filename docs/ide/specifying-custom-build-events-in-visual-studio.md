---
title: Specificare eventi di compilazione personalizzati
description: Informazioni su come è possibile eseguire automaticamente i comandi in Visual Studio prima dell'avvio o al termine di una compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19b974d9e67cb2713299928f3a7e945e9208dcd8cf8c56978a019ed98f88aea7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411958"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Specificare gli eventi di compilazione personalizzati in Visual Studio

Se si specifica un evento di compilazione personalizzato, sarà possibile eseguire automaticamente i comandi prima dell'avvio o dopo il completamento di una compilazione. Ad esempio, è possibile eseguire un file *.bat* prima dell'avvio di una compilazione o copiare nuovi file in una cartella al termine della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.

Per informazioni specifiche sul linguaggio di programmazione in uso, vedere gli argomenti seguenti:

- Visual Basic--[Procedura: Specificare eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# e F#:[procedura: Specificare eventi di compilazione (C#).](../ide/how-to-specify-build-events-csharp.md)

- Visual C++: [Specificare gli eventi di compilazione](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Sintassi

Gli eventi di compilazione seguono la stessa sintassi dei comandi DOS, ma è possibile usare macro per creare con maggiore facilità gli eventi di compilazione. Per un elenco delle macro disponibili, vedere Finestra di dialogo Riga di comando eventi [pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Per ottenere risultati ottimali, seguire questi suggerimenti di formattazione:

- Aggiungere `call` un'istruzione prima di tutti gli eventi di compilazione *eseguiti.bat* file.

   Esempio: `call C:\MyFile.bat`

   Esempio: `call C:\MyFile.bat call C:\MyFile2.bat`

- Racchiudere tra virgolette i percorsi dei file.

   Esempio (per [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Separare più comandi usando le interruzioni di riga.

- Includere i caratteri jolly, se necessario.

   Esempio: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I` nel codice sopra riportato deve essere `%%I` negli script batch.

## <a name="see-also"></a>Vedi anche

- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Finestra di dialogo Riga di comando evento pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md)
- [Procedura dettagliata: Creare un'applicazione](../ide/walkthrough-building-an-application.md)
