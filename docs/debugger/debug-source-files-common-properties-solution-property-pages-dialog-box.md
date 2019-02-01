---
title: Origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di debug | Microsoft Docs
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
ms.openlocfilehash: 63f3f5649484a9714368b4c441379241252d8f36
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024604"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione
In questa pagina delle proprietà è specificato il punto in cui il debugger cerca i file di origine durante il debug della soluzione.  
  
 Per accedere alla pagina delle proprietà **Esegui debug dei file di origine**, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Proprietà** dal menu di scelta rapida. Espandere la cartella **Proprietà comuni** e fare clic sulla pagina **Esegui debug dei file di origine**.  
  
 **Directory contenenti codice sorgente**  
 Contiene un elenco di directory in cui il debugger cerca i file di origine durante il debug della soluzione. La ricerca viene eseguita anche nelle sottodirectory delle directory specificate.  
  
 **Escludi dalla ricerca i seguenti file di origine**  
 Immettere i nomi dei file che non si desidera vengano letti dal debugger. Se il debugger trova uno di questi file in una delle directory specificate in precedenza, lo ignora. Se durante il debug viene visualizzata la finestra di dialogo **Trova origine** e si fa clic su **Annulla**, il file cercato verrà aggiunto all'elenco per evitare che il debugger continui a cercarlo.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)