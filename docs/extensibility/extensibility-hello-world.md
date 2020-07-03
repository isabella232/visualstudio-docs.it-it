---
title: Esercitazione sull'estensione Hello World | Microsoft Docs
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 796cb53ea5124662c695cce55241794802f042c0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905938"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Esercitazione: creare la prima estensione: Hello World

Questo esempio Hello World illustra come creare la prima estensione per Visual Studio. Questa esercitazione illustra come aggiungere un nuovo comando a Visual Studio.

Nel processo si apprenderà come:

* **[Creare un progetto di estendibilità](#create-an-extensibility-project)**
* **[Aggiungere un comando personalizzato](#add-a-custom-command)**
* **[Modificare il codice sorgente](#modify-the-source-code)**
* **[Eseguire](#run-it)**

Per questo esempio, si userà Visual C# per aggiungere un pulsante di menu personalizzato denominato "Say Hello World!". l'aspetto è simile al seguente:

![Comando Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [procedura dettagliata sull'estendibilità in Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, verificare di aver installato il carico di lavoro **sviluppo di estensioni di Visual Studio** , che include il modello VSIX necessario e il codice di esempio.

> [!NOTE]
> Per creare un progetto di estendibilità di Visual Studio, è possibile usare qualsiasi edizione di Visual Studio (community, Professional o Enterprise).

## <a name="create-an-extensibility-project"></a>Creare un progetto di estendibilità

::: moniker range="vs-2017"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**.

Passaggio 2: Nella casella di ricerca in alto a destra digitare "VSIX" e selezionare il **progetto VSIX**di Visual C#. Immettere "HelloWorld" per il **nome** nella parte inferiore della finestra di dialogo e selezionare **OK**.

![nuovo progetto](media/hello-world-new-project.png)

Verranno ora visualizzate la pagina Introduzione e alcune risorse di esempio.

Se è necessario uscire da questa esercitazione e tornare a questa esercitazione, è possibile trovare il nuovo progetto HelloWorld nella **pagina iniziale** della sezione **recente** .

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**. Cercare "VSIX" e selezionare il **progetto VSIX** di Visual C# e quindi **Avanti**.

Passaggio 2: Immettere "HelloWorld" per il **nome del progetto** e selezionare **Crea**.

![nuovo progetto](media/hello-world-new-project-2019.png)

A questo punto verrà visualizzato il progetto HelloWorld in **Esplora soluzioni**.

::: moniker-end

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il file manifesto *. vsixmanifest* , è possibile visualizzare le opzioni modificabili, ad esempio descrizione, autore e versione.

Passaggio 2: Fare clic con il pulsante destro del mouse sul progetto (non sulla soluzione). Nel menu di scelta rapida selezionare **Aggiungi**, quindi **nuovo elemento**.

Passaggio 3. Selezionare la sezione **Extensibility** , quindi scegliere **comando**.

Passaggio 4. Nel campo **nome** nella parte inferiore immettere un nome file, ad esempio *Command.cs*.

![comando personalizzato](media/hello-world-vsix-command.png)

Il nuovo file di comando è visibile in **Esplora soluzioni**. Nel nodo **risorse** sono disponibili altri file correlati al comando. Se, ad esempio, si desidera modificare l'immagine, il file PNG è disponibile qui.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il testo del comando e del pulsante viene generato automaticamente e non è molto interessante. È possibile modificare il file VSCT e il file CS se si desidera apportare modifiche.

* Il file VSCT è la posizione in cui è possibile rinominare i comandi, nonché definire il punto in cui vengono inseriti nel sistema di comandi di Visual Studio. Quando si Esplora il file VSCT, si noteranno i commenti che spiegano in che modo ogni sezione del codice VSCT controlla.

* Il file CS consente di definire le azioni, ad esempio il gestore di clic.

::: moniker range="vs-2017"

Passaggio 1. In **Esplora soluzioni**trovare il file vsct per il nuovo comando. In questo caso, verrà chiamato *CommandPackage. vsct*.

![vsct pacchetto di comandi](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. In **Esplora soluzioni**trovare il file vsct per il pacchetto di Visual Studio di estensione. In questo caso, verrà chiamato *HelloWorldPackage. vsct*.

::: moniker-end

Passaggio 2: Modificare il `ButtonText` parametro in `Say Hello World!` .

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

Passaggio 3. Tornare a **Esplora soluzioni** e trovare il file *Command.cs* . Nel `Execute` Metodo modificare la stringa `message` da `string.Format(..)` a `Hello World!` .

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

Assicurarsi di salvare le modifiche apportate a ogni file.

## <a name="run-it"></a>Eseguire

È ora possibile eseguire il codice sorgente nell'istanza sperimentale di Visual Studio.

Passaggio 1. Premere **F5** per eseguire il comando **Avvia debug** . Questo comando Compila il progetto e avvia il debugger, avviando una nuova istanza di Visual Studio denominata **istanza sperimentale**.

::: moniker range="vs-2017"

Nella barra del titolo di Visual Studio vengono visualizzate le parole **istanza sperimentale** .

![barra del titolo dell'istanza sperimentale](media/hello-world-exp-instance.png)

::: moniker-end

Passaggio 2: Nel menu **strumenti** dell' **istanza sperimentale**fare clic su **Say Hello World!**.

![risultato finale](media/hello-world-final-result.png)

Verrà visualizzato l'output del nuovo comando personalizzato, in questo caso la finestra di dialogo al centro dello schermo che fornisce il **Hello World.** criteri.).

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono le nozioni di base sull'uso dell'estendibilità di Visual Studio, ecco dove è possibile ottenere altre informazioni:

* [Iniziare a sviluppare estensioni di Visual Studio](starting-to-develop-visual-studio-extensions.md) : esempi, esercitazioni. e pubblicazione dell'estensione
* Novità [di Visual studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -nuove funzionalità di estendibilità in visual studio 2017
* Novità [di Visual studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) -nuove funzionalità di estendibilità in visual studio 2019
* [All'interno di Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) : informazioni dettagliate sull'estendibilità di Visual Studio
