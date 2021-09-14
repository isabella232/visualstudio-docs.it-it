---
title: Eseguire il debug di file di origine/pagine delle proprietà della soluzione
description: Accedere alla pagina delle proprietà Debug file di origine Visual Studio facendo clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliendo Proprietà > proprietà comuni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4f7e6b894d891004ca275fa4bead1de48ff421f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626543"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione
In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.

 Per accedere alla pagina delle proprietà **Esegui debug dei file di origine**, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Proprietà** dal menu di scelta rapida. Espandere la cartella **Proprietà comuni** e fare clic sulla pagina **Esegui debug dei file di origine**.

 **Directory contenenti codice sorgente** Contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione. La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.

 **Non cercare questi file di origine** Immettere i nomi di tutti i file che non si desidera che il debugger letta. Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora. Se durante il debug viene visualizzata la finestra di dialogo **Trova origine** e si fa clic su **Annulla**, il file cercato verrà aggiunto all'elenco per evitare che il debugger continui a cercarlo.

## <a name="see-also"></a>Vedi anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Preparazione e Impostazioni debugger](../debugger/debugger-settings-and-preparation.md)