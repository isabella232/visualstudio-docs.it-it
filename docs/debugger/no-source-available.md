---
title: Nessuna origine disponibile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703695"
---
# <a name="no-source-available"></a>Nessuna origine disponibile
Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare. Questa condizione si verifica, di solito, quando si fa doppio clic su un modulo per il quale non è disponibile codice sorgente nella finestra **Stack di chiamate** o **Thread**. È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione. Per impostare un punto di interruzione, utilizzare invece la finestra **Disassembly**.

 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine. Visualizzare [origine file, proprietà comuni, soluzione dialogo Pagine delle proprietà di Debug](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Individuare il codice sorgente** fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile esplorare per trovare il codice sorgente.

 **Mostra Disassembly** avvia la **finestra Disassembly**.

 **Mostra sempre disassembly per i file di origine mancanti** selezionare questa opzione per visualizzare il **finestra Disassembly** automaticamente quando è disponibile alcuna origine. È anche possibile modificare questa impostazione nella finestra di dialogo **Opzioni**, categoria **Debug**, pagina **Generale**, selezionando o deselezionando **Mostra disassembly se l'origine non è disponibile**.

## <a name="see-also"></a>Vedere anche
- [Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (estensione del debugger SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)