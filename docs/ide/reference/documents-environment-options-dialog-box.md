---
title: Documenti, Ambiente, finestra di dialogo Opzioni
description: Informazioni su come usare la pagina Ambienti nella sezione Documenti per controllare la visualizzazione dei documenti nell'IDE e gestire le modifiche esterne a documenti e file.
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5f6efebfb3cfe61707b14ed39f2ae4ca2ca79585
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625884"
---
# <a name="options-dialog-box-environment--documents"></a>Finestra di dialogo Opzioni: Documenti \> dell'ambiente

Usare la finestra di dialogo **Opzioni** per controllare la visualizzazione dei documenti nell'ambiente di sviluppo integrato (IDE) e gestire le modifiche esterne apportate a documenti e file. Per accedere a questa finestra di dialogo fare clic su **Opzioni** nel menu **Strumenti** e quindi selezionare **Ambiente** > **Documenti**.

**Rileva quando il file viene modificato al di fuori dell'ambiente**

Quando l'opzione viene selezionata, viene inviato immediatamente un messaggio per notificare che sono state apportate modifiche al file aperto da un editor all'esterno dell'IDE. Il messaggio consente di ricaricare il file dall'archiviazione.

**Ricarica i file modificati a meno che non ci siano modifiche non salvate**

Quando viene selezionata l'opzione **Rileva quando il file viene modificato al di fuori dell'ambiente** e un file aperto nell'IDE viene modificato all'esterno dell'IDE, per impostazione predefinita viene generato un messaggio di avviso. Se questa opzione viene abilitata, non vengono visualizzati avvisi e il documento viene ricaricato nell'IDE per acquisire le modifiche esterne.

**Consenti modifica dei file in sola lettura, avvisa al tentativo di salvataggio**

Quando questa opzione è abilitata, è possibile aprire e modificare un file di sola lettura. Al termine dell'operazione, usare il comando **Salva con nome** per salvare il file con un nuovo nome se si vuole salvare un record delle modifiche.

**Apri file utilizzando la directory del documento attivo**

Quando l'opzione viene abilitata, nella finestra di dialogo **Apri file** viene visualizzata la directory del documento attivo. Quando l'opzione viene deselezionata, nella finestra di dialogo **Apri file** viene visualizzata la directory usata l'ultima volta per aprire un file.

**Verifica coerenza terminazioni riga al caricamento**

Selezionare questa opzione in modo che l'editor analizzi le terminazioni di riga in un file e visualizzi una finestra di messaggio se vengono rilevate incoerenze nella formattazione delle terminazioni.

**Visualizza avviso se l'annullamento globale avrà effetto sui file modificati**

Selezionare questa opzione per visualizzare una finestra di messaggio quando il comando **Annullamento globale** esegue il rollback delle modifiche di refactoring apportate ai file che sono stati modificati dopo l'operazione di refactoring. Il ripristino dello stato pre-refactoring di un file può comportare l'annullamento delle modifiche successive apportate al file.

**Mostra file esterni in Esplora soluzioni**

Selezionare questa opzione per il nodo **File esterni** in **Esplora soluzioni**. I file esterni sono file non associati a un progetto o a una soluzione, che possono tuttavia essere visualizzati in **Esplora soluzioni** per comodità.

> [!NOTE]
> Selezionare questa opzione per abilitare il **comando Visualizza** nel browser del menu **File** per i documenti Web non inclusi nell'applicazione Web attiva.

**Elementi salvati nel progetto File esterni**

Specifica il numero di file da salvare in modo permanente nella cartella **File esterni** di **Esplora soluzioni**. Questi file vengono elencati anche se non sono più aperti in un editor. È possibile specificare un numero intero qualsiasi compreso tra 0 e 256. Il numero predefinito è 0.

Ad esempio, se si imposta questa opzione su 5 e i file esterni aperti sono 10, quando si chiudono tutti i 10 file, i primi 5 verranno ancora visualizzati nella cartella **File esterni**.

**Salva documenti come Unicode quando i dati non possono essere salvati nella tabella codici**

Se si seleziona questa opzione, i file contenenti informazioni non compatibili con la tabella codici selezionata saranno salvati in formato Unicode per impostazione predefinita.

## <a name="see-also"></a>Vedi anche

- [File esterni](../../ide/reference/miscellaneous-files.md)
- [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)
