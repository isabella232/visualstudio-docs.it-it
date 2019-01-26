---
title: Esercitazione di Hello World estensione | Microsoft Docs
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c68ddea3f92c33056ba1dc98332755dfd3bb1b9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921045"
---
# <a name="create-your-first-extension-hello-world"></a>Creare la prima estensione: Hello World

In questo esempio Hello World illustra la creazione di tua prima estensione per Visual Studio. Questa esercitazione illustra come aggiungere un nuovo comando per Visual Studio.

Nel processo, si apprenderà come:

* **[Creare un progetto di estensibilità](#create-an-extensibility-project)**
* **[Aggiungere un comando personalizzato](#add-a-custom-command)**
* **[Modificare il codice sorgente](#modify-the-source-code)**
* **[Eseguirlo](#run-it)**

In questo esempio si userà Visual c# per aggiungere che un pulsante di menu personalizzato denominato "Say Hello World!" che aspetto simile al seguente:

![Comando di Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [procedura dettagliata di estendibilità in Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di aver installato il **sviluppo di estensioni di Visual Studio** carico di lavoro che include il modello di VSIX verrà necessarie e codice di esempio.

> [!NOTE]
> È possibile usare qualsiasi edizione di Visual Studio (Community, Professional o Enterprise) per creare un progetto di estendibilità di Visual Studio.

## <a name="create-an-extensibility-project"></a>Creare un progetto di estensibilità

Passaggio 1. Dal **File** menu, fare clic su **nuovo progetto**. Nella parte inferiore della schermata, immettere il nome del progetto.

Passaggio 2. Dal **modelli** dal menu fare clic su **Visual c#**, fare clic su **estendibilità**, quindi fare clic su **progetto VSIX**.

![nuovo progetto](media/hello-world-new-project.png)

Si noterà ora la pagina introduttiva e alcune risorse di esempio.

Se è necessario lasciare questa esercitazione ed è tornato a esso, è possibile trovare il nuovo progetto HelloWorld nel **pagina iniziale** nel **recenti** sezione.

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il manifesto, è possibile vedere quali sono le opzioni sono modificabili, per istanza, i metadati, descrizione e versione.

Passaggio 2. Fare clic sul progetto (non sulla soluzione). Nel menu di scelta rapida, fare clic su **Add**, quindi fare clic su **nuovo elemento**.

Passaggio 3. Selezionare il **estendibilità** sezione e quindi fare clic su **comando personalizzato**.

Passaggio 4. Nel **Name** campo nella parte inferiore, assegnargli un nome, ad esempio *Command.cs*.

![comando personalizzato](media/hello-world-custom-command.png)

Nuovo comando è elencato nella **Esplora soluzioni** sotto il **risorse** ramo. Si tratta inoltre dove è possibile trovare altri file correlati al comando, ad esempio i file PNG e ICO se si vuole modificare l'immagine.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il pulsante che si sta aggiungendo è piuttosto generico. È possibile modificare il file VSCT CS se si desidera apportare modifiche.

* Il file VSCT è dove è possibile rinominare i comandi, nonché definire in cui escono nel sistema di comandi di Visual Studio. Durante l'esplorazione file VSCT, si noterà una grande quantità di codice commentato che spiega quali ogni sezione di controlli di codice.

* Il file CS è che consente di definire le azioni, ad esempio il gestore di clic.

Passaggio 1. Nelle **Esplora soluzioni**, trovare il file VSCT per il nuovo comando. In questo caso, verrà chiamato *CommandPackage.vsct*.

![comando pacchetto vsct](media/hello-world-command-package-vsct.png)

Passaggio 2. Modifica il `ButtonText` parametro per `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Passaggio 3. Tornare alla **Esplora soluzioni** e trovare il *Command.cs* file. Modificare la stringa `message` per il comando `string.Format(..)` a `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Assicurarsi di salvare le modifiche a ogni file.

## <a name="run-it"></a>Eseguirlo

È ora possibile eseguire il codice sorgente nell'istanza sperimentale di Visual Studio.

Passaggio 1. Fare clic su **avviare** sulla barra degli strumenti. Viene compilato il progetto e avvia il debugger, avviando una nuova istanza di Visual Studio denominato il **istanza sperimentale**.

Si noterà che le parole **istanza sperimentale** nella barra del titolo di Visual Studio.

![sulla barra del titolo istanza sperimentale](media/hello-world-exp-instance.png)

Passaggio 2. Nel **degli strumenti** dal menu del **istanza sperimentale**, fare clic su **Say Hello World!**.

![risultato finale](media/hello-world-final-result.png)

Verrà visualizzato l'output dal nuovo comando personalizzato, in questo caso la finestra di dialogo al centro dello schermo che ti offre la **Hello World!** trovata.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere appreso le nozioni di base dell'utilizzo di Extensibility di Visual Studio, ecco dove è possibile altre informazioni:

* [Iniziare a sviluppare estensioni di Visual Studio](starting-to-develop-visual-studio-extensions.md) -esempi, esercitazioni. e la pubblicazione dell'estensione
* [Novità in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -nuove funzionalità di estendibilità in Visual Studio 2017
* [All'interno di Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -informazioni dettagliate su Extensibility di Visual Studio