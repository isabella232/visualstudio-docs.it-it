---
title: Vantaggio WhiteSource Bolt
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e8b5e08178ac35e57350052e6a9076dc0f80dca6
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Attivazione del vantaggio WhiteSource Bolt nelle sottoscrizioni di Visual Studio

È possibile trovare e correggere le vulnerabilità open source e generare report esaurienti sull'inventario e sulle licenze di tutti i componenti open source nella build.  La sottoscrizione Enterprise include una sottoscrizione gratuita di sei mesi. 

1.  Per usufruire del vantaggio WhiteSource Bolt, fare clic sul collegamento **Ottieni il codice** nella parte inferiore del riquadro del vantaggio.    

    ![Riquadro del vantaggio WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Si riceverà una notifica con il codice di attivazione.  **Copiare il codice negli Appunti** e quindi fare clic su **Attiva**. 

    ![Codice del vantaggio WhiteSource Bolt ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Nella pagina Web WhiteSource fare clic sul pulsante **Activate** (Attiva) o scorrere verso il basso fino alla sezione **Activate your account** (Attiva l'account) della pagina.  

    ![Attivazione del vantaggio WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Nella sezione **Activate your account** (Attiva l'account) della pagina, l'utente viene guidato attraverso quattro passaggi:
- [Installare](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) l'estensione WhiteSource Bolt da Microsoft Visual Studio Marketplace. Se non si hanno le autorizzazioni necessarie per installare estensioni, visitare [questa pagina](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request).

    Fare clic sul pulsante **Install** (Installa) verde se si usa VSTS o sul pulsante **Download** per Team Foundation Server.  Per questo esempio si userà Visual Studio Team Services. 

    ![Installazione dell'estensione del vantaggio WhiteSource](_img\vs-whitesource\vs-whitesource-download-install.png)

- Selezionare quindi l'account VSTS che si vuole usare e fare clic su **Confirm** (Conferma).  Se non è ancora stata eseguita la configurazione di VSTS, visitare la pagina [Vantaggi](https://my.visualstudio.com/benefits) e attivare il vantaggio VSTS.

    ![Conferma dell'account del vantaggio WhiteSource](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- Si riceverà la conferma dell'installazione dell'estensione, che è ora pronta all'uso.  Fare clic su **Inizia subito** per tornare alla pagina WhiteSource Bolt e continuare.  

    ![Installazione del vantaggio WhiteSource completata](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Aprire il dashboard del progetto di Visual Studio Team Services (VSTS), fare clic sul menu **Compilazione e versione** e scegliere **WhiteSource Bolt**.

    ![Aggiunta dell'estensione del vantaggio WhiteSource](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Incollare il codice di attivazione dal riquadro del vantaggio WhiteSource Bolt e fare clic su **Activate** (Attiva). Ogni codice di attivazione può essere usato per attivare un solo progetto. 

    ![Codice di attivazione del vantaggio WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  L'attivazione è stata completata. Per la sottoscrizione rimangono 180 giorni. 
8.  È necessario aggiungere l'estensione WhiteSource Bolt ai passaggi di compilazione.  Nella [pagina di WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) è disponibile un video che illustra come effettuare questa operazione.  
9. Con la compilazione vengono generati automaticamente i report e i dashboard esaustivi seguenti:
- Dashboard delle vulnerabilità di sicurezza
- Report delle vulnerabilità di sicurezza
- Report delle librerie obsolete
- Rischi per le licenze e dashboard di conformità
- Report di inventario
