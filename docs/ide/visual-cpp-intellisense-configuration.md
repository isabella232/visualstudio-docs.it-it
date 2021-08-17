---
title: Configurare un progetto C++ per IntelliSense
description: Informazioni su come configurare manualmente il progetto C++ per ottenere il corretto funzionamento di IntelliSense usando l'IDE di Visual Studio per identificare e risolvere i problemi di IntelliSense.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 5de1e8e3faff8370343c5145e0ddbd107f0b3b82f7f2e48b901afa7e2c4377c3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399641"
---
# <a name="configure-a-c-project-for-intellisense"></a>Configurare un progetto C++ per IntelliSense

In alcuni casi, potrebbe essere necessario configurare manualmente il progetto C++ per il corretto funzionamento di IntelliSense. Per i progetti MSBuild (basati su file con estensione vcxproj), è possibile modificare le impostazioni nelle proprietà del progetto. Per i progetti non MSBuild, è possibile modificare le impostazioni nel file CppProperties.json nella directory radice del progetto. In alcuni casi, potrebbe essere necessario creare un file dei suggerimenti per aiutare IntelliSense a riconoscere le definizioni di macro. L'IDE di Visual Studio permette di identificare e correggere i problemi di IntelliSense.

## <a name="single-file-intellisense"></a>IntelliSense con singolo file

Quando si apre un file che non è incluso in un progetto, Visual Studio offre supporto per IntelliSense, ma per impostazione predefinita non viene visualizzato il controllo ortografia del codice. Se la **barra di spostamento** indica *File esterni*, questo probabilmente spiega perché non viene visualizzato il controllo ortografia nel codice non corretto o perché non è definita una macro del preprocessore.

## <a name="check-the-error-list"></a>Controllare l'elenco errori

Se un file non è aperto in modalità unico file e IntelliSense non funziona correttamente, il primo elemento da controllare è la finestra Elenco errori. Per visualizzare tutti gli errori di IntelliSense per il file di origine corrente insieme a tutti i file di intestazione inclusi, scegliere **Compilazione + IntelliSense** nell'elenco a discesa:

![VC++ IntelliSense nell'elenco errori](media/vcpp-intellisense-error-list.png)

IntelliSense produce un massimo di 1000 errori. Se nei file di intestazione sono inclusi più di 1000 errori da un file di origine, il file di origine mostra una sola istanza del controllo ortografia del codice proprio all'inizio del file di origine.

## <a name="ensure-include-paths-are-correct"></a>Verificare che i percorsi #include siano corretti

### <a name="msbuild-projects"></a>Progetti MSBuild

Se le compilazioni vengono eseguite all'esterno dell'IDE di Visual Studio e riescono, ma IntelliSense non è corretto, è possibile che la riga di comando non sia sincronizzata con le impostazioni di progetto per una o più configurazioni. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e assicurarsi che tutti i percorsi **#include** siano corretti per la configurazione e la piattaforma correnti. Se i percorsi sono identici in tutte le configurazioni e piattaforme, è possibile selezionare **Tutte le configurazioni** e **Tutte le piattaforme** e quindi verificare che i percorsi siano corretti.

![Directory di inclusione di VC++](media/vcpp-intellisense-include-paths.png)

Per visualizzare i valori correnti per compilare macro come **VC_IncludePath**, selezionare la riga Directory di inclusione e fare clic sull'elenco a discesa a destra. Scegliere quindi **\<Edit>** e fare clic sul **pulsante** Macro.

### <a name="makefile-projects"></a>progetti Makefile

Per i progetti Makefile basati sul modello di progetto NMake, scegliere **NMake** nel riquadro a sinistra e quindi scegliere **Percorso di ricerca di inclusione** nella categoria **IntelliSense**:

![Percorsi di inclusione del progetto Makefile](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Progetti Apri cartella

Per i progetti CMake, assicurarsi che i percorsi #include siano specificati correttamente per tutte le configurazioni in CMakelists.txt. Altri tipi di progetto possono richiedere un file CppProperties.json. Per altre informazioni, vedere [Configurare IntelliSense con CppProperties.json](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Assicurarsi che i percorsi siano corretti per ogni configurazione definita nel file.

Se il file CppProperties.json contiene un errore di sintassi, IntelliSense nei file interessati non sarà corretto. Visual Studio visualizzerà l'errore nella finestra di output.

## <a name="tag-parser-issues"></a>Problemi del parser di tag

Il parser di tag è un parser C++ "fuzzy" usato per l'esplorazione e lo spostamento. È molto veloce, ma non tenta di riconoscere completamente ogni costrutto di codice.

Ad esempio, non valuta le macro del preprocessore e di conseguenza può analizzare non correttamente il codice che ne fa un uso intensivo. Quando il parser di tag individua un costrutto di codice che non riconosce, può ignorare l'intera area di codice.

Esistono due modi comuni in cui questo problema si manifesta in Visual Studio:

1. Se la barra di spostamento indica una macro più interna, la definizione di funzione corrente è stata ignorata:

   ![Il parser di tag ignora la definizione di funzione](media/vcpp-intellisense-tag-parser-macro.png)

1. L'IDE offre di creare una definizione di funzione per una funzione già definita:

   ![Il parser di tag offre di definire la funzione esistente](media/vcpp-intellisense-tag-parser-function.png)

Per correggere questo tipo di problemi, aggiungere un file denominato **cpp.hint** alla radice della directory della soluzione. Per altre informazioni, vedere [File dei suggerimenti](/cpp/build/reference/hint-files).

Gli errori del parser di tag vengono visualizzati nella finestra **Elenco errori**.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Convalidare le impostazioni del progetto con la registrazione diagnostica

Per verificare se il compilatore di IntelliSense usa opzioni del compilatore corrette, tra cui percorsi di inclusione e macro del preprocessore, attivare le righe di comando della registrazione diagnostica di IntelliSense in **Strumenti > Opzioni > Editor di testo > C/C++ > Avanzate > Registrazione diagnostica**. Impostare **Abilita registrazione** su True, **Livello di registrazione** su 5 (più dettagliato) e **Filtro di registrazione** su 8 (registrazione di IntelliSense).

La finestra di output mostrerà ora le righe di comando passate al compilatore di IntelliSense. Di seguito è riportato un output di esempio:

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

Queste informazioni possono aiutare a identificare perché IntelliSense fornisce informazioni non accurate. Ad esempio, se la directory di inclusione del progetto contiene **$(MyVariable)\Include** e il log di diagnostica mostra **/I\Include** come percorso di inclusione, significa che **$(MyVariable)** non è stato valutato ed è stato rimosso dal percorso di inclusione finale.

## <a name="about-the-intellisense-build"></a>Informazioni sulla compilazione di IntelliSense

Visual Studio usa un compilatore C++ dedicato per creare e gestire il database usato da tutte le funzionalità di IntelliSense. Per sincronizzare il database di IntelliSense con il codice, Visual Studio avvia automaticamente le compilazioni solo IntelliSense come attività in background in risposta a determinate modifiche apportate nelle impostazioni del progetto o nei file di origine.

Tuttavia, in alcuni casi Visual Studio può non aggiornare il database di IntelliSense in modo tempestivo. Ad esempio, quando si esegue un comando **git pull** o **git checkout**, Visual Studio può impiegare fino a un'ora per rilevare le modifiche nei file. È possibile forzare una nuova analisi di tutti i file in una soluzione facendo clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliendo **Ripeti analisi soluzione**.

## <a name="troubleshooting-intellisense-build-failures"></a>Correzione degli errori di compilazione di IntelliSense

Una compilazione di IntelliSense non genera i file binari, ma può comunque non riuscire. Una possibile causa dell'errore riguarda i file con estensione props o targets. In Visual Studio 2017 versione 15.6 e successive vengono registrati gli errori di compilazione solo di IntelliSense nella finestra di output. Per visualizzarli, impostare **Mostra output di** su **Soluzione**:

![Finestra di output per gli errori della soluzione](media/vcpp-intellisense-output-window.png)

Il messaggio di errore può indicare di abilitare la traccia in fase di progettazione:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Se si imposta la variabile di ambiente TRACEDESIGNTIME su true e si riavvia Visual Studio, verrà visualizzato un file di log nella directory %TEMP%, che può aiutare a diagnosticare l'errore di compilazione.

Per altre informazioni sulla variabile di ambiente TRACEDESIGNTIME, vedere [Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Diagnosing-Project-System-Build-Errors.md) e [Common Project System](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Le informazioni contenute in questi articoli si applicano ai progetti C++.

## <a name="see-also"></a>Vedi anche

- [IntelliSense per Visual C++](visual-cpp-intellisense.md)
