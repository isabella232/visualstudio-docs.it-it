---
title: Esercitazione di Hello World estensione | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3beedce039d1c093b5dfebce07b09d7d3a5795dc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912312"
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

Prima di iniziare, assicurarsi di aver installato il **sviluppo di estensioni di Visual Studio** carico di lavoro, che include il modello di VSIX verrà necessarie e codice di esempio.

> [!NOTE]
> È possibile usare qualsiasi edizione di Visual Studio (Community, Professional o Enterprise) per creare un progetto di estendibilità di Visual Studio.

## <a name="create-an-extensibility-project"></a>Creare un progetto di estensibilità

::: moniker range="vs-2017"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**.

Passaggio 2. Nella casella di ricerca in alto a destra, digitare "vsix" e selezionare l'oggetto visivo C# **progetto VSIX**. Immettere "HelloWorld" per il **Name** nella parte inferiore della finestra di dialogo e selezionare **OK**.

![nuovo progetto](media/hello-world-new-project.png)

Si noterà ora la pagina introduttiva e alcune risorse di esempio.

Se è necessario lasciare questa esercitazione ed è tornato a esso, è possibile trovare il nuovo progetto HelloWorld nel **pagina iniziale** nel **recenti** sezione.

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**. Cercare "vsix" e selezionare l'oggetto visivo C# **progetto VSIX** e quindi **successiva**.

Passaggio 2. Immettere "HelloWorld" per il **nome progetto** e selezionare **crea**.

![nuovo progetto](media/hello-world-new-project-2019.png)

Il progetto HelloWorld in dovrebbe **Esplora soluzioni**.

::: moniker-end

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il *vsixmanifest* file manifesto, è possibile visualizzare quali opzioni sono modificabili, ad esempio descrizione, autore e versione.

Passaggio 2. Fare clic sul progetto (non sulla soluzione). Nel menu di scelta rapida, selezionare **Add**e quindi **nuovo elemento**.

Passaggio 3. Selezionare il **estendibilità** sezione e quindi scegliere **comando personalizzato**.

Passaggio 4. Nel **Name** campo nella parte inferiore, immettere un nome di file, ad esempio *Command.cs*.

![comando personalizzato](media/hello-world-custom-command.png)

Il nuovo file di comando è visibile nel **Esplora soluzioni**. Sotto il **risorse** nodo, sono disponibili altri file correlati ai tuoi ordini. Ad esempio, se si vuole modificare l'immagine, il file PNG viene qui.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il comando e il testo del pulsante vengono generati automaticamente e non è molto interessante. È possibile modificare il file VSCT CS se si desidera apportare modifiche.

* Il file VSCT è dove è possibile rinominare i comandi, nonché definire in cui escono nel sistema di comandi di Visual Studio. Durante l'esplorazione file VSCT, si noterà commenti che spiegano quali ogni sezione di codice controlli VSCT.

* Il file CS è che consente di definire le azioni, ad esempio il gestore di clic.

::: moniker range="vs-2017"

Passaggio 1. Nelle **Esplora soluzioni**, trovare il file VSCT per il nuovo comando. In questo caso, verrà chiamato *CommandPackage.vsct*.

![comando pacchetto vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. Nelle **Esplora soluzioni**, trovare il file VSCT per il pacchetto di estensione per Visual Studio. In questo caso, verrà chiamato *HelloWorldPackage.vsct*.

::: moniker-end

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

Passaggio 3. Tornare alla **Esplora soluzioni** e trovare il *Command.cs* file. Nel `Execute` metodo, modificare la stringa `message` dalla `string.Format(..)` a `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

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

Passaggio 1. Premere **F5** per eseguire il **Avvia debug** comando. Questo comando compila il progetto e avviare il debugger, avviando una nuova istanza di Visual Studio denominato il **istanza sperimentale**.

::: moniker range="vs-2017"

Si noterà che le parole **istanza sperimentale** nella barra del titolo di Visual Studio.

![sulla barra del titolo istanza sperimentale](media/hello-world-exp-instance.png)

::: moniker-end

Passaggio 2. Nel **degli strumenti** dal menu del **istanza sperimentale**, fare clic su **Say Hello World!**.

![risultato finale](media/hello-world-final-result.png)

Verrà visualizzato l'output dal nuovo comando personalizzato, in questo caso la finestra di dialogo al centro dello schermo che ti offre la **Hello World!** trovata.

## <a name="next-steps"></a>Passaggi successivi

Dopo avere appreso le nozioni di base dell'utilizzo di Extensibility di Visual Studio, ecco dove è possibile altre informazioni:

* [Iniziare a sviluppare estensioni di Visual Studio](starting-to-develop-visual-studio-extensions.md) -esempi, esercitazioni. e la pubblicazione dell'estensione
* [Novità in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -nuove funzionalità di estendibilità in Visual Studio 2017
* [Novità in Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) -nuove funzionalità di estendibilità in Visual Studio 2019
* [All'interno di Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -informazioni dettagliate su Extensibility di Visual Studio