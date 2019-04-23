---
title: 'Procedura: Eseguire il debug con codice sorgente di Code Center Premium | Microsoft Docs'
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
ms.openlocfilehash: 88644f3bf768f1b3467467a31edbd83e8e5f151c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039877"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Procedura: Eseguire il debug con codice sorgente di Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con il debugger di [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] è possibile eseguire il debug di codice sorgente condiviso sicuro disponibile in Microsoft MSDN Code Center Premium.  
  
 In questo argomento viene descritto come impostare Code Center Premium e come eseguire il debug del relativo codice sorgente in Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Per prepararsi all'esecuzione del debug con Code Center Premium  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Visual Studio.  
  
3. Scegliere **Opzioni** dal menu **Strumenti**.  
  
4. Nel **le opzioni** finestra di dialogo, aprire il **debug** nodo e fare clic su **generali**.  
  
5. Cancella il **Abilita Just My Code (solo gestito)** casella di controllo.  
  
6. Selezionare **Abilita il supporto di Server di origine**.  
  
7. Deselezionare **richiede i file di origine a una corrispondenza esatta tra la versione originale**.  
  
8. Sotto il **Debugging** nodo, fare clic su **simboli**.  
  
9. Nel **File di simboli (PDB), percorsi** casella, il **Server dei simboli Microsoft** casella di controllo e aggiungere i percorsi seguenti:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Assicurarsi di includere la barra finale<strong>/</strong> alla fine del percorso.  
  
     Spostare questi percorsi all'inizio dell'elenco per assicurarsi che questi simboli vengano caricati per primi.  
  
   > [!NOTE]
   >  Questi percorsi di Code Center Premium devono essere elencati per primi in modo che vengano caricati per primi. In Visual Studio 2010, è possibile spostare server sopra la **server dei simboli Microsoft** voce, ovvero il motivo per cui è necessario deselezionare la casella di controllo.  
   > 
   >  Per caricare simboli dai simboli Microsoft durante la sessione di debug, eseguire questa operazione:  
   > 
   > 1. Nel **Debug** menu, scegliere **Windows** e quindi scegliere **moduli**.  
   >    2.  Selezionare il modulo di cui si desidera caricare simboli, quindi aprire il menu di scelta rapida. Scegli **Carica simboli da** e quindi scegliere **server dei simboli Microsoft**.  
  
10. Nel **memorizza nella Cache i simboli dai server dei simboli in questa directory** casella, immettere un percorso, ad esempio `C:\symbols` in cui Code Center Premium può memorizzare nella cache di simboli. La memorizzazione nella cache dei simboli può contribuire a migliorare le prestazioni durante il debug.  
  
     Se si verificano dei problemi durante il debug del codice sorgente con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dopo avere completato questa procedura, controllare il percorso della cache per i file di simboli non aggiornati e memorizzati nella cache. Rimuovere i file di simboli non aggiornati.  
  
11. Fare clic su **OK**.  
  
12. Riavviare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per assicurarsi che le impostazioni siano state salvate in modo permanente.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Per eseguire il debug del codice sorgente utilizzando Connetti a processo  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Visual Studio.  
  
3. Aprire il progetto di Visual Studio.  
  
4. Nel **degli strumenti** menu, fare clic su **Connetti a processo**.  
  
5. Nel **Connetti a processo** finestra di dialogo, fare clic su **seleziona**.  
  
6. Nel **Seleziona tipo di codice** nella finestra di dialogo **rilevare questi tipi di codice**, selezionare **Native**, **gestito**, e **gestiti ( v4.0)**.  
  
7. Fare clic su **OK** per chiudere la **Seleziona tipo di codice** nella finestra di dialogo.  
  
8. Nel **processi disponibili** , selezionare il processo che si desidera eseguire il debug.  
  
9. Scegliere **Connetti**.  
  
10. Quando viene chiesto di confermare il certificato, fare clic su **OK**. Immettere il PIN. Se richiesto, accettare le condizioni per l'utilizzo di Code Center Premium.  
  
     Il download dei simboli può richiedere molto tempo, a seconda della velocità della rete. Sulla barra di stato verrà indicato quando tutti i simboli sono stati scaricati correttamente.  
  
11. Ripetere i passaggi di connessione per tutti i progetti gestiti nella soluzione.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Per eseguire il debug del codice sorgente da una soluzione esistente  
  
1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per la soluzione e quindi scegliere **proprietà**.  
  
2. Nella finestra di dialogo Pagine delle proprietà di soluzione, scegliere **Esegui Debug dei file di origine** nel **proprietà comuni** nodo.  
  
3. Aggiungere il seguente percorso per il **directory contenenti file di origine** elenco:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  Assicurarsi di includere la barra finale<strong>/</strong> alla fine del percorso.  
  
4. Per ogni progetto gestito nella soluzione, eseguire quanto segue:  
  
   1. In Esplora soluzioni aprire il menu di scelta rapida per il progetto e quindi scegliere **proprietà**.  
  
   2. Selezionare **Debug** e quindi scegliere **Abilita debug codice non gestito**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Per eseguire il debug della soluzione con l'origine Code Center Premium  
  
1. Nella classe `Package` impostare un punto di interruzione nel costruttore del pacchetto.  
  
2. Nel `Debug` menu, fare clic su **Avvia debug**.  
  
3. Quando si raggiunge il punto di interruzione nel costruttore del pacchetto, passare al **Stack di chiamate** finestra e pulsante destro del mouse lo stack frame dell'assembly da caricare i simboli, quindi fare clic su **Carica simboli**.  
  
     Fare doppio clic sul frame di chiamata per caricare l'origine.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Per analizzare il codice sorgente in Code Center Premium  
  
1. Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2. Avviare Internet Explorer e immettere l'URL `https://codepremium.msdn.microsoft.com`  
  
3. Cercare il codice sorgente desiderato.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Settings and Preparation](../debugger/debugger-settings-and-preparation.md)  (Impostazioni di debug e preparazione)  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
