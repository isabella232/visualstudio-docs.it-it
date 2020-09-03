---
title: Pubblicare un'estensione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201972"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procedura dettagliata: pubblicazione di un'estensione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: la raccolta di Visual Studio viene sostituita dalla Visual Studio Marketplace. Per informazioni dettagliate, vedere la versione più recente di questo argomento.

Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio in Visual Studio Gallery. Quando si aggiunge l'estensione alla raccolta, gli sviluppatori possono usare **estensioni e aggiornamenti** per individuare le estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio
 In questo caso verrà usata un'estensione VSPackage predefinita, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in C# denominato `TestPublishing` con un comando di menu. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testare l'estensione
 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug. per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, andare al menu **strumenti** e fare clic su **Gestione estensioni**. L'estensione TestPublishing dovrebbe essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **strumenti** verificare che sia visualizzato il comando test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Pubblicare l'estensione in Visual Studio Gallery
 A questo punto è possibile pubblicare l'estensione in Visual Studio Gallery.

1. Assicurarsi di aver compilato la versione di rilascio dell'estensione e che sia aggiornata.

2. In un Web browser aprire il sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. Nell'angolo in alto a destra fare clic su **Sign in (accedi**).

4. Usare l'account Microsoft per accedere. Se non si dispone di un account Microsoft, è possibile crearne uno a questo punto.

5. Fare clic su **Carica**.

6. In **Step 1: Extension Type**selezionare **Tool** e quindi fare clic su **Next**.

7. In **Step 2: upload**è possibile scegliere di caricare direttamente in Visual Studio Gallery o semplicemente aggiungere un collegamento al proprio sito Web. In questo caso selezionare **si desidera caricare lo strumento**. Verrà visualizzata la casella **selezionare il controllo** . Fare clic su **Sfoglia** e quindi selezionare TestPublish. VSIX nella cartella \bin\release del progetto. Fare clic su **Avanti**.

8. Nel **passaggio 3: informazioni di base**, vengono visualizzati i campi del file source. Extension. vsixmanifest. Selezionare una **categoria** appropriata e aggiungere i **tag** per consentire agli utenti di trovare l'estensione. Potrebbe essere necessario aggiungere una descrizione e un riepilogo più dettagliati (la lunghezza della descrizione deve essere di almeno 280 caratteri). Lasciare il **tipo di estensione** come versione di **valutazione** **non è un'estensione Microsoft e una** categoria di **costo** .

9. Leggere il contratto di contributo nella parte inferiore della pagina **e selezionare Accetto**.

10. Fare clic su **Crea contributo**. Viene visualizzata la pagina in cui si troverà l'estensione in Visual Studio Gallery, con un messaggio che indica che la pagina non è ancora stata pubblicata.

11. Fare clic su **Pubblica**.

12. Cercare l'estensione nella raccolta di Visual Studio. Verrà visualizzato l'elenco per l'estensione TestPublish.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installare l'estensione da Visual Studio Gallery
 Ora che l'estensione è pubblicata, installarla in Visual Studio ed eseguirne il test.

1. In Visual Studio scegliere **estensioni e aggiornamenti**dal menu **strumenti** .

2. Fare clic su **online** e quindi cercare TestPublish. Verrà visualizzato l'elenco per l'estensione TestPublish.

3. Fare clic su **Download**. Dopo aver scaricato l'estensione, fare clic su **Installa**.

4. Per completare l'installazione, riavviare Visual Studio.

## <a name="removing-the-extension"></a>Rimozione dell'estensione
 È possibile rimuovere l'estensione da Visual Studio Gallery e dal computer.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Per rimuovere l'estensione da Visual Studio Gallery

1. Aprire il sito Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. Nell'angolo in alto a destra fare clic su **My extenions**. Viene visualizzato l'elenco di TestPublish.

3. Fare clic su **Elimina**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere **Gestione estensioni** dal menu **Strumenti**.

2. Selezionare TestPublish e quindi fare clic su **Disinstalla**.

3. Per completare la disinstallazione, riavviare Visual Studio.
