---
title: Nessuna origine disponibile | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd7643dd7334a220d1e5c78ef12bddf07af11f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519198"
---
# <a name="no-source-available"></a>Nessuna origine disponibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Nessuna origine disponibile](https://docs.microsoft.com/visualstudio/debugger/no-source-available).  
  
Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare. La causa è facendo doppio clic su un modulo che non dispone di codice sorgente nel **finestra Stack di chiamate** oppure **finestra thread**. È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione. Se è necessario impostare un punto di interruzione, usare il **nella finestra Disassembly** invece.  
  
 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine. Visualizzare [origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di Debug](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Sfogliare per trovare codice sorgente**  
 Fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile cercare il codice sorgente.  
  
 **Mostra Disassembly**  
 Viene avviata il **nella finestra Disassembly**.  
  
 **Mostra sempre disassembly per i file di origine mancanti**  
 Selezionare questa opzione per visualizzare il **nella finestra Disassembly** automaticamente quando è disponibile alcuna origine. Questa impostazione può essere modificata anche nel **opzioni** della finestra di dialogo **debug** categoria **generali** pagina, selezionando o deselezionando **Mostra disassembly se origine non è disponibile**.  
  
## <a name="see-also"></a>Vedere anche  
 [Origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di debug](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (estensione del debugger SOS)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)



