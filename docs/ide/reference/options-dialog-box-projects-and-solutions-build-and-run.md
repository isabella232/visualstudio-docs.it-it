---
title: Finestra di dialogo Opzioni, progetti e soluzioni, compila ed Esegui
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff1ec236c85aeaeed655c611a88cead4380258f0
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037712"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Finestra di dialogo Opzioni: progetti e soluzioni \> Compila ed Esegui

In questa finestra di dialogo è possibile specificare il numero massimo di progetti C++ o C# che è possibile compilare allo stesso tempo, determinati comportamenti di compilazione predefiniti e alcune impostazioni del log di compilazione. Per accedere a queste opzioni, selezionare **strumenti**  >  **Opzioni** espandere **progetti e soluzioni**, quindi selezionare **Compila ed Esegui**.

**Numero massimo di compilazioni di progetto parallele**

Specifica il numero massimo di progetti C++ e C# che è possibile compilare contemporaneamente. Per ottimizzare il processo di compilazione, il numero massimo di compilazioni di progetti in parallelo viene impostato automaticamente sul numero di CPU del computer. Il valore massimo è 32.

**Compila progetti di avvio e dipendenze solo in fase di esecuzione**

Compila solo il progetto di avvio e le relative dipendenze quando si usa il tasto **F5**, si seleziona il comando di menu **Debug** > **Avvia debug** o i comandi applicabili del menu **Genera**. Se non si seleziona questa opzione, vengono compilati tutti i progetti e le relative dipendenze.

**Durante l'esecuzione, quando i progetti non sono aggiornati**

*Si applica solo ai progetti C++.*

Quando si esegue un progetto con **F5** o il comando **Debug** > **Avvia debug**, l'impostazione predefinita **Richiedi compilazione** visualizza un messaggio se una configurazione di progetto non è aggiornata. Selezionare **Compila sempre** per compilare il progetto ogni volta che viene eseguito. Selezionare **Non compilare mai** per eliminare tutte le compilazioni automatiche quando si esegue un progetto.

**Durante l'esecuzione, quando si verificano errori di compilazione o distribuzione**

*Si applica solo ai progetti C++.*

Quando si esegue un progetto con **F5** o il comando **Debug** > **Avvia debug**, l'impostazione predefinita **Richiedi avvio** visualizza un messaggio se un progetto deve essere eseguito anche se la compilazione non è riuscita. Selezionare **Avvia versione precedente** per avviare automaticamente l'ultima compilazione valida. In questo modo è possibile che il codice in esecuzione non corrisponda al codice sorgente. Selezionare **Non avviare** per eliminare il messaggio.

**Per nuove soluzioni utilizza il progetto selezionato come progetto di avvio**

Se questa opzione è impostata, le nuove soluzioni usano il progetto selezionato come progetto di avvio.

**Livello di dettaglio output in compilazione progetto MSBuild**

Determina la quantità di informazioni del processo di compilazione che viene visualizzata nella finestra **Output**.

**Livello di dettaglio file di log di compilazione progetto MSBuild**

*Si applica solo ai progetti C++.*

Determina la quantità di informazioni scritte nel file di log di compilazione, disponibile in * \\ \<ProjectName> \Debug \\ \<ProjectName> . log*.

## <a name="see-also"></a>Vedi anche

- [Compilazione e creazione](../../ide/compiling-and-building-in-visual-studio.md)
- [Finestra di dialogo Opzioni, Progetti e soluzioni](projects-and-solutions-options-dialog-box.md)
- [Opzioni (finestra di dialogo), Progetti e soluzioni, Progetti Web](options-dialog-box-projects-and-solutions-web-projects.md)