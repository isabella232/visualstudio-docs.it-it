---
title: Nessuna origine disponibile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697803"
---
# <a name="no-source-available"></a>Nessuna origine disponibile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare. Questa condizione si verifica, di solito, quando si fa doppio clic su un modulo per il quale non è disponibile codice sorgente nella finestra **Stack di chiamate** o **Thread**. È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione. Per impostare un punto di interruzione, utilizzare invece la finestra **Disassembly**.  
  
 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine. Vedere [eseguire il debug di file di origine, proprietà comuni, finestra di dialogo Pagine delle proprietà della soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Sfoglia per trovare il codice sorgente**  
 Fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile cercare il codice sorgente.  
  
 **Mostra disassembly**  
 Apre la finestra **Disassembly**.  
  
 **Mostra sempre disassembly per i file del codice sorgente mancanti**  
 Selezionare questa opzione per visualizzare automaticamente la finestra **Disassembly** quando non è disponibile alcuna origine. È anche possibile modificare questa impostazione nella finestra di dialogo **Opzioni**, categoria **Debug**, pagina **Generale**, selezionando o deselezionando **Mostra disassembly se l'origine non è disponibile**.  
  
## <a name="see-also"></a>Vedere anche  
 [File di origine di debug, proprietà comuni, finestra di dialogo Pagine delle proprietà della soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (estensione del debugger SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
