---
title: "Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 010a842af8f45572123298d29540c28624f394b4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770563"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procedura dettagliata: pubblicazione di un'estensione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: la raccolta di Visual Studio verrà sostituita da Visual Studio Marketplace. Vedere la versione più recente di questo argomento per informazioni dettagliate.

  
Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio in Visual Studio Gallery. Quando si aggiunge l'estensione alla raccolta, gli sviluppatori possono utilizzare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio  
 In questo caso si userà un'estensione VSPackage predefinito, ma gli stessi passaggi sono validi per ogni tipo di estensione.  
  
1.  Creare un pacchetto VSPackage in c# denominato `TestPublishing` che dispone di un comando di menu. Per altre informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="test-the-extension"></a>Testare l'estensione  
 Prima di distribuire l'estensione, compilare e testare per verificare che sia installato correttamente nell'istanza sperimentale di Visual Studio.  
  
1.  In Visual Studio, avviare il debug. Per aprire un'istanza sperimentale di Visual Studio.  
  
2.  Nell'istanza sperimentale, passare al **degli strumenti** dal menu **gestore estensioni del**. L'estensione TestPublishing dovrebbe essere visualizzato nel riquadro centrale e abilitato.  
  
3.  Nel **strumenti** menu, assicurarsi che venga visualizzato il comando di test.  
  
## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Pubblicare l'estensione per Visual Studio Gallery  
 A questo punto è possibile pubblicare l'estensione per Visual Studio Gallery.  
  
1.  Assicurarsi di avere compilato la versione dell'estensione e che sia aggiornato.  
  
2.  In un Web browser aprire il sito Web [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) .  
  
3.  Nell'angolo superiore destro, fare clic su **SIGN IN**.  
  
4.  Usare l'account Microsoft per accedere. Se non hai un account Microsoft, è possibile creare uno a questo punto.  
  
5.  Fare clic su **Upload**.  
  
6.  Nelle **passaggio 1: tipo di estensione**, selezionare **strumento** e quindi fare clic su **Avanti**.  
  
7.  Nelle **passaggio 2: caricare**, è possibile scegliere di caricare direttamente in Visual Studio Gallery o è sufficiente aggiungere un collegamento al proprio sito Web. In questo caso selezionare **desidero caricare lo strumento**. Il **selezionare il controllo** verrà visualizzata la finestra. Fare clic su **esplorare** e quindi selezionare TestPublish.vsix nella cartella \bin\Release del progetto. Scegliere **Avanti**.  
  
8.  Nelle **passaggio 3: informazioni di base**, vengono visualizzati i campi nel file vsixmanifest. Selezionare un'opzione appropriata **categoria** e aggiungere **tag** per consentire agli utenti di trovare l'estensione. È possibile aggiungere un riepilogo e una descrizione (la descrizione deve essere almeno 280 caratteri) più dettagliate. Lasciare **tipo di estensione** come **non è un'estensione di Microsoft** e **categorie costi** come **versione di valutazione**.  
  
9. L'accordo di contributo nella parte inferiore della pagina leggere e controllare **accetto**.  
  
10. Fare clic su **crea contributo**. Verrà visualizzata la pagina che avrà l'estensione in Visual Studio Gallery, con un messaggio che la pagina non è ancora stata pubblicata.  
  
11. Fare clic su **Pubblica**.  
  
12. Raccolta di Visual Studio per l'estensione di ricerca. L'elenco per l'estensione TestPublish dovrebbe essere visualizzato.  
  
## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Installare l'estensione da Visual Studio Gallery  
 Ora che la pubblicazione dell'estensione, installarlo in Visual Studio e testarlo.  
  
1.  In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.  
  
2.  Fare clic su **Online** e quindi cercare TestPublish. L'elenco per l'estensione TestPublish dovrebbe essere visualizzato.  
  
3.  Scegliere **Download**. Dopo aver scaricato l'estensione, fare clic su **Installa**.  
  
4.  Per completare l'installazione, riavviare Visual Studio.  
  
## <a name="removing-the-extension"></a>Rimozione dell'estensione  
 È possibile rimuovere l'estensione da Visual Studio Gallery e dal computer.  
  
#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Per rimuovere l'estensione da Visual Studio Gallery  
  
1.  Aprire il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=194329) sito Web.  
  
2.  Nell'angolo superiore destro, fare clic su **Extenions My**. Viene visualizzato l'elenco per TestPublish.  
  
3.  Fare clic su **Elimina**.  
  
#### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer  
  
1.  In Visual Studio scegliere **Gestione estensioni** dal menu **Strumenti**.  
  
2.  Selezionare TestPublish e quindi fare clic su **Disinstalla**.  
  
3.  Per completare la disinstallazione, riavviare Visual Studio.

