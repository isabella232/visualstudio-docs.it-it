---
title: 'Procedura: Eseguire il debug di codice sorgente di .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a627c2f0880aee9906e3478b268d688c59b7d090
ms.sourcegitcommit: 6efb9378a82924cb133912d207c6da4bd5a0b9c2
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2018
ms.locfileid: "53443912"
---
# <a name="how-to-debug-net-framework-source"></a>Procedura: Eseguire il debug del codice sorgente di .NET Framework

Per eseguire il debug di codice sorgente di .NET Framework, è necessario:

- Abilitare l'esecuzione di codice sorgente di .NET Framework.  
  
- Accedere ai simboli di debug per il codice. 
  
  È possibile scegliere di scaricare i simboli di debug immediatamente, o impostare le opzioni per il download in un secondo momento. Se è non scaricare immediatamente simboli, sarà scaricare al successivo avvio di debug dell'app. Durante il debug, è anche possibile usare la **moduli** oppure **Stack di chiamate** windows per scaricare e caricare i simboli.  
  
### <a name="to-enable-stepping-into-net-framework-source"></a>Per abilitare l'esecuzione di istruzioni origine .NET Framework 
  
1. Sotto **degli strumenti** (o **Debug**) > **opzioni** > **debug** > **generale**, selezionare **origine abilitare .NET Framework l'esecuzione di istruzioni**.  
   
   - Se Just My Code è attivato, viene visualizzata una finestra di dialogo con un avviso indicante che Just My Code è stato disabilitato. Scegliere **OK**.  
   
   - Se non è stato una cache di simboli locale impostare, una finestra di dialogo di avviso indica che è stata impostata una cache di simboli predefinito. Scegliere **OK**.  
   
1. Selezionare **OK** per chiudere la **opzioni** finestra di dialogo.
  
### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Per impostare o modificare percorsi di origine del simbolo e il comportamento di caricamento

1. Selezionare il **simboli** categoria sotto **Tools** (o **Debug**) > **opzioni** > **debug**.  
  
1. Nel **simboli** nella pagina **percorsi dei file (con estensione pdb) di simboli**, selezionare **server dei simboli Microsoft** ai simboli di accesso dal server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altri percorsi dei simboli e modificare l'ordine di caricamento. 
   
1. Per modificare la cache di simboli locali, modificare o selezionare un percorso diverso in **memorizza nella Cache i simboli in questa directory**.  
   
1. Per scaricare immediatamente simboli, selezionare **carica tutti i simboli**. Questo pulsante è disponibile solo durante il debug.  
   
   Se a questo punto non si scaricano i simboli, essi verranno scaricati al successivo che avvio del debug.  
   
1. Selezionare **OK** per chiudere la **opzioni** finestra di dialogo.  
  
### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Per caricare i simboli dalla Stack di chiamate o moduli di windows  
  
1. Durante il debug, aprire la finestra selezionando **Debug** > **Windows** > **moduli** (o premere **Ctrl + Alt + U**) oppure **Debug** > **Windows** > **Stack di chiamate** (**Ctrl + Alt + C**). 
   
1. Fare doppio clic su un modulo per il quale non sono stati caricati i simboli. Nel **moduli** della finestra, lo stato di caricamento dei simboli: il **stato simboli** colonna. Nel **Stack di chiamate** della finestra, stato: il **stato Frame** colonna e il frame è grigio. 
   
   - Selezionare **caricare i simboli** dal menu per individuare e caricare i file di simboli da una cartella nel computer. 
   
   - Selezionare **informazioni sul caricamento simboli** per mostrare le posizioni, il debugger di eseguire la ricerca dei simboli.  
   
   - Selezionare **impostazioni simboli** per aprire il **simboli** pagina. Nel **simboli** nella pagina **percorsi dei file (con estensione pdb) di simboli**, selezionare **server dei simboli Microsoft** ai simboli di accesso dal server di simboli Microsoft pubblici. Selezionare i pulsanti della barra degli strumenti per aggiungere altri percorsi dei simboli e modificare l'ordine di caricamento. Selezionare **OK** per chiudere la finestra di dialogo. 
  
### <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)