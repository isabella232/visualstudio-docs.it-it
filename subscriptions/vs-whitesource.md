---
title: Vantaggio WhiteSource Bolt | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Informazioni su come attivare la sottoscrizione di WhiteSource Bolt inclusa nella sottoscrizione di Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 981d6a655a203a7d44728fa7d12761fba2918d76
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935777"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt nelle sottoscrizioni di Visual Studio

È possibile trovare e correggere le vulnerabilità open source e generare report esaurienti sull'inventario e sulle licenze di tutti i componenti open source nella build. Alcune sottoscrizioni di Visual Studio includono sei mesi di accesso gratuito.

## <a name="activation-steps"></a>Procedura di attivazione

1. Per attivare il vantaggio di WhiteSource Bolt, accedere a [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs) .

2. Individuare il riquadro WhiteSource Bolt nella sezione Strumenti e fare clic sul collegamento **Ottieni il codice** nella parte inferiore del riquadro del vantaggio.
   > [!div class="mx-imgBorder"]
   > ![Riquadro del vantaggio WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-tile.png)

3. Si riceverà una notifica con il codice di attivazione.  **Copiare il codice negli Appunti** e quindi fare clic su **Attiva**.
   > [!div class="mx-imgBorder"]
   > ![Codice del vantaggio WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-code.png)

4. Nella pagina Web WhiteSource fare clic sul pulsante **Activate** (Attiva) o scorrere verso il basso fino alla sezione **Activate your account** (Attiva l'account) della pagina.
   > [!div class="mx-imgBorder"]
   > ![Attivazione del vantaggio WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. Nella sezione **Activate your account** (Attiva l'account) della pagina, l'utente viene guidato attraverso quattro passaggi:

   - [Installare](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) l'estensione WhiteSource Bolt da Microsoft Visual Studio Marketplace. Se non si è autorizzati a installare le estensioni, vedere [Install free extensions for Azure DevOps Services](/azure/devops/marketplace/install-vsts-extension?view=vsts) (Installare le estensioni gratuite per Azure DevOps Services).


~~~
Click the green **Install** button if you are using Azure DevOps Services, or the **Download** button for Team Foundation Server.  For this example, we will use Azure DevOps Services.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Extension](_img\vs-whitesource\vs-whitesource-download-install.png)

- Next, select the Azure DevOps organization you want to use and click **Confirm**.  (If you have not yet set up Azure DevOps Services, visit the [Benefits](https://my.visualstudio.com/benefits) page and activate your Azure DevOps Services benefit.)

> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Confirm Account](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- You’ll receive a confirmation that the extension is installed and ready to use.  Click **Get started** to return to the WhiteSource Bolt page and continue.
> [!div class="mx-imgBorder"]
> ![WhiteSource Benefit Install Complete](_img\vs-whitesource\vs-whitesource-install-complete.png)
~~~

5. Aprire il dashboard del progetto Azure DevOps, fare clic sul menu **Azure Pipelines** e scegliere **WhiteSource Bolt**.
   > [!div class="mx-imgBorder"]
   > ![Aggiunta dell'estensione del vantaggio WhiteSource](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. Incollare il codice di attivazione dal riquadro del vantaggio WhiteSource Bolt e fare clic su **Activate** (Attiva). Ogni codice di attivazione può essere usato per attivare un solo progetto.
   > [!div class="mx-imgBorder"]
   > ![Codice di attivazione del vantaggio WhiteSource Bolt](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. L'attivazione è stata completata. Per la sottoscrizione rimangono 180 giorni.

8. È necessario aggiungere l'estensione WhiteSource Bolt ai passaggi di compilazione.  Nella [pagina di WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) è disponibile un video che illustra come effettuare questa operazione.

9. Con la compilazione vengono generati automaticamente i report e i dashboard esaustivi seguenti:
    - Dashboard delle vulnerabilità di sicurezza
    - Report delle vulnerabilità di sicurezza
    - Report delle librerie obsolete
    - Rischi per le licenze e dashboard di conformità
    - Report di inventario

## <a name="eligibility"></a>Idoneità

| Livello di sottoscrizione                                                 |     Canali                                            | Vantaggio                                                          | Rinnovabile?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard, cloud annuale)   | VL, Azure, Retail, NFR<sup>1</sup> selezionato | 6 mesi       |  Yes          |
| Visual Studio Professional (Standard, cloud annuale) | VL, Azure, Retail                                       | Non disponibile                                                           |N/D         |
| Visual Studio Test Professional (Standard)                         | VL, Retail                                              | Non disponibile                                             |  N/D         |
| MSDN Platforms (Standard)                                          | VL, Retail                                              | Non disponibile                                              | N/D         |
| Visual Studio Dev Essentials | N/D  | Non disponibile |N/D |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensile) | Azure                                       | Non disponibile                                                           |N/D|

<sup>1</sup>   *Include: Microsoft Partner Network (Enterprise).  Non include: altre versioni Not for Resale (NFR), Visual Studio Industry Partner (VSIP), FTE, MCT Software & Services Developer, BizSpark, Imagine, Microsoft Valued Professional (MVP), Region Director (RD), MCT Software & Services, Microsoft Partner Network (Professional).*

Non si è certi della sottoscrizione in uso?  Connettersi a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) per visualizzare tutte le sottoscrizioni assegnate al proprio indirizzo di posta elettronica. Se non sono visualizzate tutte le sottoscrizioni, è possibile che una o più sottoscrizioni siano assegnate a un indirizzo di posta elettronica diverso.  È necessario accedere con tale indirizzo di posta elettronica per visualizzare le sottoscrizioni.

## <a name="support-resources"></a>Risorse di supporto

-  Serve aiuto con WhiteSource Bolt?  Chat con un rappresentante WhiteSource Bolt in tempo reale all'indirizzo https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  Per assistenza per le vendite, le sottoscrizioni, gli account e la fatturazione per le sottoscrizioni di Visual Studio, contattare il [servizio di supporto per le sottoscrizioni](https://visualstudio.microsoft.com/subscriptions/support/) di Visual Studio.
-  Per domande sull'IDE di Visual Studio, Azure DevOps Services o altri prodotti e servizi Visual Studio,  visitare il [sito del supporto di Visual Studio](https://visualstudio.microsoft.com/support/).