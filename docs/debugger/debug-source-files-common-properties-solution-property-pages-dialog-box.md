---
title: Eseguire il debug delle pagine delle proprietà di proprietà/soluzione/comuni di file di origine
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631ec8ed4f6b5cd410b3af51c55fa87935b9cddf
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263138"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione
In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.

 Per accedere alla pagina delle proprietà **Esegui debug dei file di origine**, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Proprietà** dal menu di scelta rapida. Espandere la cartella **Proprietà comuni** e fare clic sulla pagina **Esegui debug dei file di origine**.

 **Directory contenenti codice sorgente** contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione. La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.

 **Non cercare questi file di origine** immettere i nomi di tutti i file che non si desidera vengano letti dal debugger. Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora. Se durante il debug viene visualizzata la finestra di dialogo **Trova origine** e si fa clic su **Annulla**, il file cercato verrà aggiunto all'elenco per evitare che il debugger continui a cercarlo.

## <a name="see-also"></a>Vedere anche

- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)