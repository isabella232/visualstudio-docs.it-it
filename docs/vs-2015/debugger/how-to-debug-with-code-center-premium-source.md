---
title: "Procedura: eseguire il debug con l'origine Code Center Premium | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839351"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Procedura: eseguire il debug con codice sorgente di Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con il debugger di [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] è possibile eseguire il debug di codice sorgente condiviso sicuro disponibile in Microsoft MSDN Code Center Premium.  
  
 In questo argomento viene descritto come impostare Code Center Premium e come eseguire il debug del relativo codice sorgente in Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Per prepararsi all'esecuzione del debug con Code Center Premium  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Visual Studio.  
  
3. Scegliere **Opzioni** dal menu **Strumenti**.  
  
4. Nella finestra di dialogo **Opzioni** aprire il nodo **debug** e fare clic su **generale**.  
  
5. Deselezionare la casella di controllo **abilita Just My Code (solo gestito)** .  
  
6. Selezionare **Abilita supporto del server di origine**.  
  
7. Deselezionare **Richiedi corrispondenza esatta dei file di origine con la versione originale**.  
  
8. Nel nodo **debug** fare clic su **simboli**.  
  
9. Nella casella **percorsi dei file di simboli (con estensione pdb)** deselezionare la casella di controllo **simboli server Microsoft** e aggiungere i percorsi seguenti:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Assicurarsi di includere la barra finale <strong>/</strong> alla fine del percorso.  
  
     Spostare questi percorsi all'inizio dell'elenco per assicurarsi che questi simboli vengano caricati per primi.  
  
   > [!NOTE]
   > Questi percorsi di Code Center Premium devono essere elencati per primi in modo che vengano caricati per primi. In Visual Studio 2010 non è possibile spostare i server sopra la voce **Server dei simboli Microsoft** , motivo per cui è necessario deselezionare la casella di controllo.  
   > 
   >  Per caricare simboli dai simboli Microsoft durante la sessione di debug, eseguire questa operazione:  
   > 
   > 1. Scegliere **finestre** dal menu **debug** , quindi **moduli**.  
   >    2.  Selezionare il modulo di cui si desidera caricare simboli, quindi aprire il menu di scelta rapida. Scegliere **Carica simboli da** , quindi scegliere **Server dei simboli Microsoft**.  
  
10. Nella casella **memorizza nella cache i simboli dai server di simboli in questa directory** immettere un percorso, ad esempio, in `C:\symbols` cui Code Center Premium può memorizzare nella cache i simboli. La memorizzazione nella cache dei simboli può contribuire a migliorare le prestazioni durante il debug.  
  
     Se si verificano dei problemi durante il debug del codice sorgente con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dopo avere completato questa procedura, controllare il percorso della cache per i file di simboli non aggiornati e memorizzati nella cache. Rimuovere i file di simboli non aggiornati.  
  
11. Fare clic su **OK**.  
  
12. Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per assicurarsi che le impostazioni siano state salvate in modo permanente.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Per eseguire il debug del codice sorgente utilizzando Connetti a processo  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Visual Studio.  
  
3. Aprire il progetto di Visual Studio.  
  
4. Scegliere **Connetti a processo**dal menu **strumenti** .  
  
5. Nella finestra di dialogo **Connetti a processo** fare clic su **Seleziona**.  
  
6. Nella finestra di dialogo **Seleziona tipo di codice** , **in rileva questi tipi di codice**, selezionare **nativo**, **gestito**e **gestito (v 4.0)**.  
  
7. Fare clic su **OK** per chiudere la finestra di dialogo **Seleziona tipo di codice** .  
  
8. Nella casella **processi disponibili** selezionare il processo di cui si desidera eseguire il debug.  
  
9. Scegliere **Connetti**.  
  
10. Quando viene richiesto di confermare il certificato, fare clic su **OK**. Immettere il PIN. Se richiesto, accettare le condizioni per l'utilizzo di Code Center Premium.  
  
     Il download dei simboli può richiedere molto tempo, a seconda della velocità della rete. Sulla barra di stato verrà indicato quando tutti i simboli sono stati scaricati correttamente.  
  
11. Ripetere i passaggi di connessione per tutti i progetti gestiti nella soluzione.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Per eseguire il debug del codice sorgente da una soluzione esistente  
  
1. In **Esplora soluzioni**aprire il menu di scelta rapida per la soluzione, quindi scegliere **Proprietà**.  
  
2. Nella finestra di dialogo Pagine delle proprietà della soluzione scegliere **Esegui debug dei file di origine** nel nodo **Proprietà comuni** .  
  
3. Aggiungere il percorso seguente all'elenco **directory che contiene i file di origine** :  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Assicurarsi di includere la barra finale <strong>/</strong> alla fine del percorso.  
  
4. Per ogni progetto gestito nella soluzione, eseguire quanto segue:  
  
   1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto, quindi scegliere **Proprietà**.  
  
   2. Selezionare **debug** , quindi scegliere **Abilita debug del codice**non gestito.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Per eseguire il debug della soluzione con l'origine Code Center Premium  
  
1. Nella classe `Package` impostare un punto di interruzione nel costruttore del pacchetto.  
  
2. Nel `Debug` menu fare clic su **Avvia debug**.  
  
3. Quando si raggiunge il punto di interruzione nel costruttore del pacchetto, passare alla finestra **stack di chiamate** e fare clic con il pulsante destro del mouse sul stack frame dell'assembly da cui si desidera caricare i simboli, quindi scegliere **Carica simboli**.  
  
     Fare doppio clic sul frame di chiamata per caricare l'origine.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Per analizzare il codice sorgente in Code Center Premium  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Internet Explorer e immettere l'URL `https://codepremium.msdn.microsoft.com`  
  
3. Cercare il codice sorgente desiderato.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni e preparazione del debugger](../debugger/debugger-settings-and-preparation.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
