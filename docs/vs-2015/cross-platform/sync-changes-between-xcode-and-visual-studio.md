---
title: Sincronizzare le modifiche tra XCode e Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 42352ba4c5260c4b13a4cb3c6875d3469efcf404
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573383"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Sincronizzare le modifiche tra XCode e Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il componente Microsoft Visual C++ per lo sviluppo di app per dispositivi mobili include funzionalità remote per la sincronizzazione del lavoro tra PC e Mac. Quando Visual Studio e i computer Mac vengono associati, sono disponibili nuove opzioni per i progetti di applicazioni iOS in Visual Studio che è possibile usare per aprire il progetto in XCode, spostare il codice tra XCode e Visual Studio e pulire la directory temporanea del progetto XCode.

 Per usare le opzioni Computer remoto, il progetto deve essere un progetto di applicazione iOS e Visual Studio deve essere associato al Mac. Per informazioni sui prerequisiti e istruzioni su come eseguire l'associazione di un Mac, vedere [Installare e configurare gli strumenti per la compilazione con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Menu Computer remoto
 In **Esplora soluzioni** fare clic con il pulsante destro del mouse su un progetto di applicazione iOS per visualizzare il menu di scelta rapida. Selezionare **Computer remoto** per visualizzare le opzioni remote disponibili.

 ![Voce di menu Computer remoto in Esplora soluzioni](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Questi comandi consentono di aprire il progetto in XCode, spostare le modifiche locali o l'intero progetto tra Visual Studio e XCode e pulire i file temporanei nel computer remoto.

### <a name="open-in-xcode"></a>Apri in Xcode
 Per aprire il progetto in XCode da Visual Studio, scegliere il sottomenu **Computer remoto**, quindi scegliere **Apri in Xcode** per aprire il progetto selezionato nel computer remoto associato. Viene usato il server vcremote per aprire XCode nel Mac e passare a una directory temporanea creata nel Mac che contiene una copia del progetto. Verrà visualizzata una finestra di dialogo di Visual Studio che mostra la directory temporanea usata per il progetto. Le azioni eseguite nel computer remoto sono anche indicate nella finestra **Output** di Visual Studio. Per visualizzarle, può essere necessario selezionare **Computer remoto Visual C++** nell'elenco a discesa **Mostra output di**, disponibile nella parte superiore della finestra **Output**.

 ![Azioni nel computer remoto visualizzate nella finestra Output.](../cross-platform/media/cppmdd-u2-remotemachine-output.png "CPPMDD_U2_RemoteMachine_Output")

 Nel Mac è possibile usare tutti gli strumenti di XCode per modificare il codice, le risorse, gli storyboard e le azioni. In Visual Studio, il progetto di applicazione iOS è contrassegnato come "Aperto in XCode" per indicare che potrebbero essere apportate modifiche nel computer remoto. Dopo aver completato le modifiche, è possibile usare i comandi Pull da computer remoto o Pull incrementale da computer remoto per copiare nuovamente le modifiche nel progetto di Visual Studio.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Push in computer remoto e Push incrementale in computer remoto
 Se sono state apportate modifiche al progetto di applicazione iOS in Visual Studio, è possibile usare i comandi Push in computer remoto e Push incrementale in computer remoto per spostare i file di progetto modificati nel computer remoto associato. Il comando Push in computer remoto copia tutti i file di progetto nel computer remoto. Il comando Push incrementale in computer remoto copia solo i file modificati nel computer remoto. Per i progetti di grandi dimensioni con piccole modifiche, il comando incrementale consente di risparmiare tempo e larghezza di banda.

 Per copiare i file di progetto nel Mac, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto**, quindi scegliere **Push in computer remoto** o **Push incrementale in computer remoto** per copiare i file di progetto da Visual Studio nel Mac.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Pull da computer remoto e Pull incrementale da computer remoto
 Dopo aver apportato modifiche al progetto in XCode, spostare nuovamente le modifiche in Visual Studio per mantenere sincronizzati i progetti.

 Per copiare i file di progetto dal Mac, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto**, quindi scegliere **Pull da computer remoto** o **Pull incrementale da computer remoto** per copiare i file di progetto dal Mac in Visual Studio.

### <a name="clean-remote"></a>Pulisci computer remoto
 È possibile usare il comando Pulisci computer remoto per eliminare i file nella directory temporanea del progetto nel computer remoto. Il contenuto della directory, inclusi eventuali file di origine o prodotti di compilazione, viene rimosso dal Mac. Prima di usare il comando Pulisci computer remoto, assicurarsi di avere sincronizzato le modifiche da mantenere in Visual Studio tramite il comando Pull da computer remoto o Pull incrementale da computer remoto.

 Per pulire la directory temporanea del progetto nel computer remoto, nella finestra **Esplora soluzioni** di Visual Studio fare clic sul progetto di applicazione iOS per aprire il menu di scelta rapida. Selezionare **Computer remoto** quindi scegliere **Pulisci computer remoto** per rimuovere i file della directory del progetto dal Mac.
