---
title: Eseguire ClickOnce debug di app che usano System.Deployment.Application
description: Informazioni su come usare e personalizzare le funzionalità ClickOnce di distribuzione tramite l'accesso al modello a oggetti di distribuzione fornito da System.Deployment.Application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: d91b59b6f4eb86c905fcddd28dc5298b1a18f761
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080663"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Debug di applicazioni ClickOnce in cui si usa System.Deployment.Application
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] la distribuzione consente di configurare la modalità di aggiornamento di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione. Tuttavia, se è necessario usare e personalizzare le funzionalità di distribuzione avanzate, sarà necessario accedere al modello a oggetti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] di distribuzione fornito da <xref:System.Deployment.Application> . È possibile usare <xref:System.Deployment.Application> le API per attività avanzate, ad esempio:

- Creazione di un'opzione "Aggiorna ora" nell'applicazione

- Download condizionali su richiesta di vari componenti dell'applicazione

- Aggiornamenti integrati direttamente nell'applicazione

- Garantire che l'applicazione client sia sempre aggiornata

  Poiché le API funzionano solo quando un'applicazione viene distribuita con la tecnologia , l'unico modo per eseguirne il debug è distribuire l'applicazione usando , collegarsi ad essa e quindi <xref:System.Deployment.Application> [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguirne il debug. Può essere difficile collegare il debugger abbastanza presto, perché questo codice viene spesso eseguito all'avvio dell'applicazione e viene eseguito prima di poter collegare il debugger. Una soluzione consiste nell'inserire interruzioni (o arresti, per i progetti Visual Basic) prima del codice di controllo dell'aggiornamento o del codice su richiesta.

  La tecnica di debug consigliata è la seguente:

1. Prima di iniziare, assicurarsi che i file di simboli (con estensione pdb) e di origine siano archiviati.

2. Distribuire la versione 1 dell'applicazione.

3. Creare una nuova soluzione vuota. Scegliere **Nuovo** dal menu **File**, quindi **Progetto**. Nella finestra **di dialogo Project** nuova applicazione aprire il nodo Altri **Project** e quindi selezionare la cartella **Visual Studio soluzioni.** Nel riquadro **Modelli** selezionare **Soluzione vuota.**

4. Aggiungere il percorso di origine archiviato alle proprietà per questa nuova soluzione. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo della soluzione e quindi **scegliere Proprietà.** Nella finestra **di dialogo** Pagine delle proprietà selezionare Esegui debug dei file **di origine** e quindi aggiungere la directory del codice sorgente archiviato. In caso contrario, il debugger troverà i file di origine non aggiornati, poiché i percorsi dei file di origine vengono registrati nel file con estensione pdb. Se il debugger usa file di origine non aggiornati, viene visualizzato un messaggio che informa che l'origine non corrisponde.

5. Assicurarsi che il debugger sia in grado di *trovare i file con estensione pdb.* Se sono stati distribuiti con l'applicazione, il debugger li trova automaticamente. Prima viene sempre cercata accanto all'assembly in questione. In caso contrario, sarà necessario aggiungere il percorso di archivio ai percorsi del file di simboli (con estensione  **pdb).** Per accedere a questa opzione, scegliere Opzioni dal **menu** Strumenti **,** quindi aprire il nodo Debug e fare clic su **Simboli**.

6. Eseguire il debug di ciò che accade `CheckForUpdate` tra le chiamate al metodo e `Download` / `Update` .

    Ad esempio, il codice di aggiornamento potrebbe essere il seguente:

   ```vb
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

8. Provare a collegare il debugger all'applicazione versione 1 durante il download di un aggiornamento per la versione 2. In alternativa, è possibile usare `System.Diagnostics.Debugger.Break` il metodo o semplicemente in `Stop` Visual Basic. Naturalmente, non è consigliabile lasciare queste chiamate al metodo nel codice di produzione.

    Si supponga, ad esempio, di sviluppare un'applicazione Windows Forms e di avere un gestore eventi per questo metodo con la logica di aggiornamento. Per eseguire il debug, è sufficiente collegarsi prima che venga premuto il pulsante, quindi impostare un punto di interruzione (assicurarsi di aprire il file archiviato appropriato e impostarvi il punto di interruzione).

   Usare la proprietà per richiamare le API solo quando l'applicazione viene distribuita. Le API non devono essere richiamate <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> durante il debug in <xref:System.Deployment.Application> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche
- <xref:System.Deployment.Application>