---
title: Finestra di output
description: Informazioni sulla finestra Output e su come vengono visualizzati i messaggi di stato per varie funzionalità nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6ff6f19139d8874d252bcaa540062c0d230ed2d10221bb5371c2180b23edfe75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387239"
---
# <a name="output-window"></a>Output (finestra)

Nella finestra **Output** vengono visualizzati messaggi di stato per diverse funzionalità dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment). Per aprire la finestra **Output**, nella barra dei menu scegliere **Visualizza** > **Output** oppure premere **CTRL**+**ALT**+**O**.

## <a name="toolbar"></a>Barra degli strumenti

I controlli seguenti vengono visualizzati nella barra degli strumenti della finestra **Output**.

### <a name="show-output-from"></a>Mostra output di

Visualizza uno o più riquadri di output da visualizzare. Potrebbero essere disponibili diversi riquadri di informazioni, a seconda dello strumento dell'IDE da cui è stata usata la finestra **Output** per recapitare messaggi all'utente.

### <a name="find-message-in-code"></a>Trova messaggio nel codice

Sposta il punto di inserimento nell'editor di codice nella riga che contiene l'errore di compilazione selezionato.

### <a name="go-to-previous-message"></a>Vai al messaggio precedente

Consente di spostare l'attivazione nella finestra **Output** all'errore di compilazione precedente e di spostare il punto di inserimento nell'editor di codice alla riga che contiene l'errore di compilazione.

### <a name="go-to-next-message"></a>Vai al messaggio successivo

Consente di spostare l'attivazione nella finestra **Output** all'errore di compilazione successivo e di spostare il punto di inserimento nell'editor di codice alla riga che contiene l'errore di compilazione.

### <a name="clear-all"></a>Cancella tutto

Cancella tutto il testo dal riquadro **Output**.

### <a name="toggle-word-wrap"></a>Attiva/Disattiva a capo automatico

Attiva e disattiva la funzione A capo automatico nel riquadro **Output**. Quando la funzione A capo automatico è attiva, il testo contenuto in voci particolarmente lunghe che si estende oltre l'area di visualizzazione verrà visualizzato nella riga successiva.

## <a name="output-pane"></a>Riquadro di output

Nel riquadro **Output** selezionato nell'elenco **Mostra output di** viene visualizzato l'output dell'origine indicata.

## <a name="route-messages-to-the-output-window"></a>Indirizzare i messaggi alla finestra Output

Per visualizzare la finestra **Output** ogni volta che si compila un progetto, nella finestra di dialogo **Opzioni** della pagina **Progetti e soluzioni** > **Generale** selezionare **Mostra finestra di output a inizio compilazione**. A questo punto, con un file di codice aperto per la modifica, scegliere **Vai al messaggio successivo** e **Vai al messaggio precedente** nella barra degli strumenti della finestra **Output** per selezionare le voci nel riquadro **Output**. Durante l'operazione, il punto di inserimento nell'editor di codice passa alla riga di codice in cui si è verificato il problema selezionato.

Alcuni comandi e funzionalità dell'IDE richiamati nella [finestra Comando](../../ide/reference/command-window.md) indirizzano l'output alla finestra **Output**. L'output di strumenti esterni, come file con estensione *bat* e *com*, generalmente genere visualizzato nella finestra di comando, viene indirizzato a un riquadro **Output** quando si seleziona l'opzione **Usa finestra di output** in [Gestire strumenti esterni](../../ide/managing-external-tools.md). Nei riquadri **Output** possono essere visualizzati anche molti altri tipi di messaggi. Ad esempio, quando la sintassi Transact-SQL in una stored procedure viene controllata in base a un database di destinazione, i risultati vengono visualizzati nella finestra **Output**.

È anche possibile programmare applicazioni personalizzate per scrivere messaggi di diagnostica in fase di esecuzione in un riquadro **Output**. A tale scopo, usare i membri della classe <xref:System.Diagnostics.Debug> o <xref:System.Diagnostics.Trace> nello spazio dei nomi <xref:System.Diagnostics> dell'API .NET. I membri della classe <xref:System.Diagnostics.Debug> visualizzano l'output quando si compilano configurazioni di debug della soluzione o del progetto, mentre i membri della classe <xref:System.Diagnostics.Trace> visualizzano l'output quando si compilano configurazioni di debug o di rilascio. Per altre informazioni, vedere [Messaggi diagnostici nella finestra di output](../../debugger/diagnostic-messages-in-the-output-window.md).

In C++ è possibile creare istruzioni ed eventi di compilazione personalizzati i cui avvisi ed errori vengono visualizzati e conteggiati nel riquadro **Output**. Premendo **F1** in una riga di output, è possibile visualizzare un argomento della Guida appropriato. Per altre informazioni, vedere [Formattare l'output di un'istruzione di compilazione personalizzata](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Comportamento dello scorrimento

Se si usa lo scorrimento automatico nella finestra **Output** e quindi si naviga usando il mouse o i tasti di direzione, lo scorrimento automatico viene arrestato. Per riprendere lo scorrimento automatico, premere  + **CTRL+FINE.**

## <a name="see-also"></a>Vedi anche

- [Messaggi di diagnostica nella finestra Output](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Procedura: Controllare la finestra di output](/previous-versions/ht6z4e28(v=vs.140))
- [Compilare](../../ide/compiling-and-building-in-visual-studio.md)
- [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
- [Panoramica della libreria di classi](/dotnet/standard/class-library-overview)