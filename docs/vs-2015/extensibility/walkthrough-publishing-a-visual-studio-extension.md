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
ms.openlocfilehash: 0d32428c7a7b1f481771aacaf3e2b0dadfde5db6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001355"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: Raccolta di Visual Studio verrà sostituita da Visual Studio Marketplace. Vedere la versione più recente di questo argomento per informazioni dettagliate.


Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio in Visual Studio Gallery. Quando si aggiunge l'estensione alla raccolta, gli sviluppatori possono utilizzare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio
 In questo caso si userà un'estensione VSPackage predefinito, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1.  Creare un pacchetto VSPackage in C# denominato `TestPublishing` che dispone di un comando di menu. Per altre informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Testare l'estensione
 Prima di distribuire l'estensione, compilare e testare per verificare che sia installato correttamente nell'istanza sperimentale di Visual Studio.

1.  In Visual Studio, avviare il debug. Per aprire un'istanza sperimentale di Visual Studio.

2.  Nell'istanza sperimentale, passare al **degli strumenti** dal menu **gestore estensioni del**. L'estensione TestPublishing dovrebbe essere visualizzato nel riquadro centrale e abilitato.

3.  Nel **strumenti** menu, assicurarsi che venga visualizzato il comando di test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Pubblicare l'estensione per Visual Studio Gallery
 A questo punto è possibile pubblicare l'estensione per Visual Studio Gallery.

1.  Assicurarsi di avere compilato la versione dell'estensione e che sia aggiornato.

2.  In un web browser, aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sito Web.

3.  Nell'angolo superiore destro, fare clic su **SIGN IN**.

4.  Usare l'account Microsoft per accedere. Se non hai un account Microsoft, è possibile creare uno a questo punto.

5.  Fare clic su **Upload**.

6.  In **passaggio 1: Tipo di estensione**, selezionare **strumento** e quindi fare clic su **successivo**.

7.  In **passaggio 2: Caricare**, è possibile scegliere di caricare direttamente in Visual Studio Gallery o è sufficiente aggiungere un collegamento al proprio sito Web. In questo caso selezionare **desidero caricare lo strumento**. Il **selezionare il controllo** verrà visualizzata la finestra. Fare clic su **esplorare** e quindi selezionare TestPublish.vsix nella cartella \bin\Release del progetto. Scegliere **Avanti**.

8.  In **passaggio 3: Informazioni di base**, vengono visualizzati i campi nel file vsixmanifest. Selezionare un'opzione appropriata **categoria** e aggiungere **tag** per consentire agli utenti di trovare l'estensione. È possibile aggiungere un riepilogo e una descrizione (la descrizione deve essere almeno 280 caratteri) più dettagliate. Lasciare **tipo di estensione** come **non è un'estensione di Microsoft** e **categorie costi** come **versione di valutazione**.

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

1.  Aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/) sito Web.

2.  Nell'angolo superiore destro, fare clic su **Extenions My**. Viene visualizzato l'elenco per TestPublish.

3.  Fare clic su **Elimina**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1.  In Visual Studio scegliere **Gestione estensioni** dal menu **Strumenti**.

2.  Selezionare TestPublish e quindi fare clic su **Disinstalla**.

3.  Per completare la disinstallazione, riavviare Visual Studio.
