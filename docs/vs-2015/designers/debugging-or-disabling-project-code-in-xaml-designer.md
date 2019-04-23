---
title: Debug o disabilitazione del codice del progetto nella finestra di progettazione XAML | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8773b9f80299c1a46b6a57506d09f9f4ca32b998
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060774"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Debug o disabilitazione del codice del progetto nella finestra di progettazione XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In molti casi, le eccezioni non gestite nella finestra di progettazione XAML possono essere causate dal codice del progetto che prova ad accedere a proprietà o metodi che restituiscono valori diversi o funzionano in modi diversi quando l'applicazione è in esecuzione nella finestra di progettazione. È possibile risolvere queste eccezioni eseguendo il debug del codice del progetto in un'altra istanza di Visual Studio oppure impedirle temporaneamente disabilitando il codice del progetto nella finestra di progettazione.  
  
 Il codice del progetto include:  
  
- Controlli personalizzati e controlli utente  
  
- Librerie di classi  
  
- Convertitori di valori  
  
- Associazioni in base ai dati della fase di progettazione generati dal codice del progetto  
  
  Quando il codice del progetto è disabilitato, Visual Studio visualizza segnaposto, ad esempio il nome della proprietà per un'associazione in cui i dati non sono più disponibili o un segnaposto per un controllo che non è più in esecuzione.  
  
  ![Finestra di dialogo Eccezione non gestita](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Per determinare se il codice del progetto sta causando un'eccezione  
  
1. Nella finestra di dialogo dell'eccezione non gestita fare clic sul collegamento **Fare clic qui per ricaricare la finestra di progettazione** .  
  
2. Sulla barra dei menu fare clic su **Debug**, **Avvia debug** per compilare ed eseguire l'applicazione.  
  
     Se l'applicazione viene compilata ed eseguita correttamente, l'eccezione in fase di progettazione potrebbe essere causata dal codice del progetto in esecuzione nella finestra di progettazione.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Per eseguire il debug del codice del progetto in esecuzione nella finestra di progettazione  
  
1. Nella finestra di dialogo dell'eccezione non gestita fare clic sul collegamento **Fare clic qui per consentire l'esecuzione del codice del progetto e ricaricare la finestra di progettazione** .  
  
2. In Gestione attività di Windows fare clic sul pulsante **Termina attività** per chiudere tutte le istanze della finestra di progettazione XAML di Visual Studio attualmente in esecuzione.  
  
     ![Istanze della finestra di progettazione XAML in TaskManager](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3. In Visual Studio aprire la pagina XAML che contiene il codice o il controllo di cui si vuole eseguire il debug.  
  
4. Aprire una nuova istanza di Visual Studio e quindi aprire una seconda istanza del progetto.  
  
5. Impostare un punto di interruzione nel codice del progetto.  
  
6. Sulla barra dei menu della nuova istanza di Visual Studio fare clic su **Debug**, **Connetti a processo**.  
  
7. Nella finestra di dialogo **Connetti a processo** scegliere **XDesProc.exe** nell'elenco **Processi disponibili**e quindi fare clic sul pulsante **Connetti** .  
  
     ![Processo della finestra di progettazione XAML](../designers/media/xaml-attach.png "XAML_Attach")  
  
     Questo è il processo per la finestra di progettazione XAML nella prima istanza di Visual Studio.  
  
8. Sulla barra dei menu della prima istanza di Visual Studio fare clic su **Debug**, **Avvia debug**.  
  
     È ora possibile eseguire le istruzioni del codice in esecuzione nella finestra di progettazione.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Per disabilitare il codice del progetto nella finestra di progettazione  
  
- Nella finestra di dialogo dell'eccezione non gestita fare clic sul collegamento **Fare clic qui per consentire l'esecuzione del codice del progetto e ricaricare la finestra di progettazione** .  
  
- In alternativa, sulla barra degli strumenti nella finestra di progettazione XAML fare clic sul pulsante **Disabilita il codice del progetto** .  
  
     ![Pulsante Disabilita il codice del progetto](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     È possibile attivare di nuovo il pulsante per riabilitare il codice del progetto.  
  
    > [!NOTE]
    >  Per i progetti destinati a processori ARM o X64, Visual Studio non può eseguire il codice del progetto nella finestra di progettazione, quindi il pulsante **Disabilita il codice del progetto** è disabilitato nella finestra di progettazione.  
  
- Entrambe le opzioni comporteranno il ricaricamento della finestra di progettazione e quindi la disabilitazione di tutto il codice per il progetto associato.  
  
    > [!NOTE]
    >  La disabilitazione del codice del progetto può provocare una perdita di dati della fase di progettazione. In alternativa, è possibile eseguire il debug del codice in esecuzione nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md)
