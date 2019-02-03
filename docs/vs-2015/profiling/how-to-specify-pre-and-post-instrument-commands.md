---
title: 'Procedura: Specificare comandi pre- e post-strumentazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b548265959ed2be10feb1096d7dc92d95a6cfed0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792834"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Procedura: Specificare comandi pre- e post-strumentazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile specificare i comandi da eseguire prima o dopo che vengano instrumentati i file binari in una sessione di prestazioni. Tutti i comandi eseguibili dalla riga di comando possono essere specificati come eventi pre-strumentazione o post-strumentazione. Ad esempio, è possibile specificare comandi che automatizzano la riapposizione della firma di un assembly con una chiave con nome sicuro in un file batch eseguito dopo la strumentazione dei file binari.  
  
 È possibile specificare comandi per tutti i file binari instrumentati nell'esecuzione della profilatura o per singoli file binari. Tuttavia, è possibile specificare un solo comando pre-strumentazione da eseguire prima e un solo comando post-strumentazione da eseguire dopo il processo di strumentazione. Non è possibile specificare comandi sia per tutti i file binari che per singoli file binari. Quando si specificano comandi per tutti i file binari, i comandi vengono eseguiti prima o dopo la strumentazione di ogni file binario della sessione.  
  
 **Requirements**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  La directory di lavoro nella quale vengono eseguiti i comandi dipende dal sistema operativo in cui è in esecuzione [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] e dalla piattaforma di destinazione dell'applicazione profilata.  
  
  **Computer a 32 bit**  
  
  Nei computer a 32 bit la directory predefinita per gli strumenti di profilatura è Unità\Programmi\Microsoft Visual Studio 10.0\Team Tools\Performance Tools.  
  
  **Computer a 64 bit**  
  
  Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione profilata:  
  
- La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:  
  
   *Unità*\Programmi (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools  
  
- La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:  
  
   *Unità*\Programmi (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>Per specificare comandi pre-strumentazione  
  
1.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Per specificare comandi pre-strumentazione per tutti i file binari in una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.  
  
    -   Per specificare comandi pre-strumentazione per un file binario specifico, fare clic con il pulsante destro del mouse sul nome del file binario nell'elenco **Destinazioni** della sessione di prestazioni e quindi selezionare **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic su **Strumentazione**.  
  
3.  Digitare il comando nella casella di testo **Riga di comando** in **Eventi pre-strumentazione**.  
  
    > [!NOTE]
    >  È possibile fare clic sul pulsante con i puntini di sospensione **(...)** adiacente alla casella **Riga di comando** per individuare e selezionare il file con estensione exe, cmd o bat appropriato.  
  
4.  Fare clic su **OK**.  
  
     Per disabilitare l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**. Per modificare le impostazioni del compilatore o del linker, usare le pagine delle proprietà del progetto.  
  
### <a name="to-specify-post-instrument-commands"></a>Per specificare comandi post-strumentazione  
  
1.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Per specificare comandi post-strumentazione per tutti i file binari in una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni** e quindi fare clic con il pulsante destro del mouse e selezionare **Proprietà**.  
  
    -   Per specificare comandi post-strumentazione per un file binario specifico, fare clic con il pulsante destro del mouse sul nome del file binario nell'elenco **Destinazioni** della sessione di prestazioni e quindi selezionare **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic su **Strumentazione**.  
  
3.  Digitare il comando nella casella di testo **Riga di comando** in **Eventi post-strumentazione**.  
  
    > [!NOTE]
    >  È possibile fare clic sul pulsante con i puntini di sospensione **(...)** adiacente alla casella **Riga di comando** per individuare e selezionare il file con estensione exe, cmd o bat appropriato.  
  
4.  Fare clic su **OK**.  
  
     Per disabilitare l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**. Per modificare le impostazioni del compilatore o del linker, usare le pagine delle proprietà del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
