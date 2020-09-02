---
title: Debug di applicazioni ClickOnce che utilizzano System. Deployment. Application | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0b12faf451d3ed9bb70e2bb1ec6c8503cfb86d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187789"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>Debug di applicazioni ClickOnce in cui si utilizza System.Deployment.Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione consente di configurare la modalità di aggiornamento di un'applicazione. Tuttavia, se è necessario utilizzare e personalizzare [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le funzionalità di distribuzione avanzate, sarà necessario accedere al modello a oggetti di distribuzione fornito da <xref:System.Deployment.Application> . È possibile usare le <xref:System.Deployment.Application> API per le attività avanzate, ad esempio:  
  
- Creazione di un'opzione "Aggiorna ora" nell'applicazione  
  
- Download condizionali su richiesta di diversi componenti dell'applicazione  
  
- Aggiornamenti integrati direttamente nell'applicazione  
  
- Garanzia che l'applicazione client sia sempre aggiornata  
  
  Poiché le <xref:System.Deployment.Application> API funzionano solo quando un'applicazione viene distribuita con la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnologia, l'unico modo per eseguirne il debug consiste nel distribuire l'applicazione usando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , connettersi, quindi eseguirne il debug. Può essere difficile alporre il debugger abbastanza presto, perché questo codice viene spesso eseguito quando l'applicazione viene avviata ed eseguita prima di poter alleghiare il debugger. Una soluzione consiste nell'inserire interruzioni (o arrestare, per Visual Basic progetti) prima del codice di controllo dell'aggiornamento o del codice su richiesta.  
  
  La tecnica di debug consigliata è la seguente:  
  
1. Prima di iniziare, assicurarsi che i file di simboli (con estensione pdb) e i file di origine vengano archiviati.  
  
2. Distribuire la versione 1 dell'applicazione.  
  
3. Creare una nuova soluzione vuota. Scegliere **Nuovo** dal menu **File**, quindi **Progetto**. Nella finestra di dialogo **nuovo progetto** aprire il nodo **altri tipi di progetto** , quindi selezionare la cartella **soluzioni di Visual Studio** . Nel riquadro **modelli** selezionare **soluzione vuota**.  
  
4. Aggiungere il percorso di origine archiviato alle proprietà per la nuova soluzione. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, quindi scegliere **Proprietà**. Nella finestra di dialogo **pagine delle proprietà** selezionare **debug dei file di origine**, quindi aggiungere la directory del codice sorgente archiviato. In caso contrario, il debugger troverà i file di origine non aggiornati, perché i percorsi dei file di origine vengono registrati nel file con estensione pdb. Se il debugger usa file di origine obsoleti, viene visualizzato un messaggio che informa che l'origine non corrisponde.  
  
5. Verificare che il debugger possa trovare i file con estensione pdb. Se sono stati distribuiti con l'applicazione, il debugger li troverà automaticamente. Viene sempre visualizzato in primo luogo accanto all'assembly in questione. In caso contrario, sarà necessario aggiungere il percorso di archiviazione ai **percorsi dei file di simboli (con estensione pdb)** . per accedere a questa opzione, scegliere **Opzioni**dal menu **strumenti** , quindi aprire il nodo **debug** e fare clic su **simboli**.  
  
6. Eseguire il debug di ciò che accade tra le `CheckForUpdate` `Download` / `Update` chiamate al metodo e.  
  
    Il codice di aggiornamento, ad esempio, potrebbe essere il seguente:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Distribuire la versione 2.  
  
8. Tentativo di connessione del debugger all'applicazione versione 1 durante il download di un aggiornamento per la versione 2. In alternativa, è possibile usare il `System.Diagnostics.Debugger.Break` metodo o semplicemente `Stop` in Visual Basic. Naturalmente, non è consigliabile lasciare queste chiamate al metodo nel codice di produzione.  
  
    Si supponga, ad esempio, che si stia sviluppando una Windows Forms Application e che sia presente un gestore eventi per questo metodo con la logica di aggiornamento. Per eseguire il debug, è sufficiente connettersi prima di premere il pulsante, quindi impostare un punto di interruzione (assicurarsi di aprire il file archiviato appropriato e impostare il punto di interruzione).  
  
   Utilizzare la <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> proprietà per richiamare le <xref:System.Deployment.Application> API solo quando viene distribuita l'applicazione; le API non devono essere richiamate durante il debug in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Deployment.Application>
