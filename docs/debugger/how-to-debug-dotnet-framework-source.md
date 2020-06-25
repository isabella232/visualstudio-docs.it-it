---
title: Come eseguire il debug di .NET Framework origine | Microsoft Docs
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3f043aae44231608fb514e87a05717f4aeb924bc
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350095"
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: Eseguire il debug del codice sorgente di .NET Framework

Per eseguire il debug di .NET Framework origine, è necessario:

- Abilitare l'esecuzione di un'istruzione nell'origine .NET Framework.

- Hanno accesso ai simboli di debug per il codice.

  È possibile scegliere di scaricare i simboli di debug immediatamente oppure impostare le opzioni per il download successivo. Se i simboli non vengono scaricati immediatamente, verranno scaricati al successivo avvio del debug dell'app. Durante il debug, è anche possibile usare i **moduli** o le finestre **dello stack di chiamate** per scaricare e caricare i simboli.

### <a name="to-enable-stepping-into-net-framework-source"></a>Per abilitare l'esecuzione di un'istruzione .NET Framework origine

1. In **strumenti** (o **debug**) > **Opzioni**  >  di**debug**  >  **generale**selezionare **Abilita .NET Framework l'esecuzione**di un'istruzione all'origine.

   - Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Fare clic su **OK**.

   - Se non è stata impostata una cache di simboli locale, viene visualizzata una finestra di dialogo di avviso che indica che è stata impostata una cache di simboli predefinita. Fare clic su **OK**.

1. Selezionare **OK** per chiudere la finestra di dialogo **Opzioni** .

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Per impostare o modificare i percorsi di origine dei simboli e il comportamento di caricamento

1. Selezionare la categoria **simboli** in **strumenti** (o **debug**) > **Opzioni**  >  **debug**.

1. Nella pagina **simboli** , in percorsi di file di simboli **(con estensione pdb)**, selezionare Server dei simboli **Microsoft** per accedere ai simboli dai server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altre posizioni dei simboli e modificare l'ordine di caricamento.

1. Per modificare la cache dei simboli locali, modificare o selezionare un percorso diverso sotto i **simboli della cache in questa directory**.

1. Per scaricare immediatamente i simboli, selezionare **carica tutti i simboli**. Questo pulsante è disponibile solo durante il debug.

   Se non si scaricano i simboli adesso, verranno scaricati al successivo avvio del debug.

1. Selezionare **OK** per chiudere la finestra di dialogo **Opzioni** .

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Per caricare i simboli dalle finestre moduli o stack di chiamate

1. Durante il debug, aprire la finestra selezionando **debug**  >  **Windows**  >  **moduli** Windows (oppure premere **CTRL + ALT + U**) o **eseguire il debug**  >  **Windows**  >  **dello stack di chiamate** Windows (**CTRL + ALT + C**).

1. Fare clic con il pulsante destro del mouse su un modulo per cui non sono stati caricati simboli Nella finestra **moduli** lo stato di caricamento dei simboli si trova nella colonna **stato simboli** . Nella finestra **stack di chiamate** lo stato è nella colonna **stato frame** e il frame è disattivato.

   - Selezionare **Carica simboli** dal menu per individuare e caricare i file di simboli da una cartella nel computer.

   - Selezionare **informazioni sul caricamento** dei simboli per visualizzare le posizioni in cui il debugger ha cercato i simboli.

   - Selezionare **Impostazioni simboli** per aprire la pagina **simboli** . Nella pagina **simboli** , in percorsi di file di simboli **(con estensione pdb)**, selezionare Server dei simboli **Microsoft** per accedere ai simboli dai server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altre posizioni dei simboli e modificare l'ordine di caricamento. Selezionare **OK** per chiudere la finestra di dialogo.

### <a name="see-also"></a>Vedi anche
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)