---
title: Esercitazione sull'estensione di Hello World Documenti Microsoft
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711654"
---
# <a name="create-your-first-extension-hello-world"></a>Creare la prima estensione: Hello WorldCreate your first extension: Hello World

In questo esempio Hello World viene illustrata la creazione della prima estensione per Visual Studio.This Hello World example walks you through creating your first extension for Visual Studio. Questa esercitazione illustra come aggiungere un nuovo comando a Visual Studio.This tutorial shows you how to add a new command to Visual Studio.

Nel processo, imparerai come:

* **[Creare un progetto di estendibilitàCreate an extensibility project](#create-an-extensibility-project)**
* **[Aggiungere un comando personalizzato](#add-a-custom-command)**
* **[Modificare il codice sorgente](#modify-the-source-code)**
* **[Eseguire](#run-it)**

Per questo esempio, si userà Visual C, per aggiungere un pulsante di menu personalizzato denominato "Say Hello World!" che assomiglia a questo:

![Comando Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Questo articolo si applica a Visual Studio in Windows.This article applies to Visual Studio on Windows. Per Visual Studio per Mac, vedere Procedura dettagliata di [estensibilità in Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di aver installato il carico di lavoro di **sviluppo di estensioni** di Visual Studio, che include il modello VSIX necessario e il codice di esempio.

> [!NOTE]
> È possibile utilizzare qualsiasi edizione di Visual Studio (Community, Professional o Enterprise) per creare un progetto di estendibilità di Visual Studio.You can use any edition of Visual Studio (Community, Professional, or Enterprise) to create a Visual Studio extensibility project.

## <a name="create-an-extensibility-project"></a>Creare un progetto di estendibilitàCreate an extensibility project

::: moniker range="vs-2017"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**.

Passaggio 2. Nella casella di ricerca in alto a destra, digitare "vsix" e selezionare il **progetto VSIX**di Visual C. Immettere "HelloWorld" come **Nome** nella parte inferiore della finestra di dialogo e selezionare **OK**.

![nuovo progetto](media/hello-world-new-project.png)

Verrà visualizzata la pagina Introduzione e alcune risorse di esempio.

Se è necessario uscire da questa esercitazione e tornare ad essa, è possibile trovare il nuovo progetto HelloWorld nella **pagina iniziale** nella sezione **Recenti.**

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**. Cercare "vsix" e selezionare il **progetto VSIX** di Visual C, quindi **Avanti**.

Passaggio 2. Immettere "HelloWorld" come nome del **progetto** e selezionare **Crea**.

![nuovo progetto](media/hello-world-new-project-2019.png)

Verrà visualizzato il progetto HelloWorld in **Esplora soluzioni**.

::: moniker-end

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il file manifesto *vsixmanifest,* è possibile visualizzare le opzioni modificabili, ad esempio descrizione, autore e versione.

Passaggio 2. Fare clic con il pulsante destro del mouse sul progetto (non sulla soluzione). Scegliere **Aggiungi**dal menu di scelta rapida, quindi **Nuovo elemento**.

Passaggio 3. Selezionare la sezione **Estendibilità** e quindi scegliere **Comando**.

Passaggio 4. Nel campo **Nome** nella parte inferiore, immettere un nome di file, ad esempio *Command.cs*.

![comando personalizzato](media/hello-world-vsix-command.png)

Il nuovo file di comando è visibile in **Esplora soluzioni.** Nel nodo **Risorse** sono disponibili altri file correlati al comando. Ad esempio, se si desidera modificare l'immagine, il file PNG è qui.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il comando e il testo del pulsante vengono generati automaticamente e non molto interessanti. È possibile modificare il file VSCT e il file CS se si desidera apportare modifiche.

* Il file VSCT è dove è possibile rinominare i comandi, nonché definire dove vanno nel sistema di comandi di Visual Studio.The VSCT file is where you can rename your commands, as well as define where they go in the Visual Studio command system. Durante l'esplorazione del file VSCT, si noteranno commenti che spiegano ciò che ogni sezione dei controlli del codice VSCT.

* Il file CS è dove è possibile definire le azioni, ad esempio il gestore di clic.

::: moniker range="vs-2017"

Passaggio 1. In **Esplora soluzioni**individuare il file VSCT per il nuovo comando. In questo caso, verrà chiamato *CommandPackage.vsct*.

![pacchetto di comandi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. In **Esplora soluzioni**individuare il file VSCT per il pacchetto VS con estensione. In questo caso, verrà chiamato *HelloWorldPackage.vsct*.

::: moniker-end

Passaggio 2. Modificare `ButtonText` il `Say Hello World!`parametro in .

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

Passaggio 3. Tornare a **Esplora soluzioni** e individuare il *file di Command.cs.* Nel `Execute` metodo modificare la `message` `string.Format(..)` stringa `Hello World!`da a .

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

È ora possibile eseguire il codice sorgente nell'istanza sperimentale di Visual Studio.You can now run the source code in the Visual Studio Experimental Instance.

Passaggio 1. Premere **F5** per eseguire il comando **Avvia debug.** Questo comando consente di compilare il progetto e avviare il debugger, avviando una nuova istanza di Visual Studio denominata **Istanza sperimentale**.

::: moniker range="vs-2017"

Vedrai le parole **Istanza sperimentale** nella barra del titolo di Visual Studio.

![barra del titolo dell'istanza sperimentale](media/hello-world-exp-instance.png)

::: moniker-end

Passaggio 2. Nel menu **Strumenti** **dell'istanza sperimentale**fare clic su **Say Hello World!**.

![risultato finale](media/hello-world-final-result.png)

Dovresti vedere l'output del tuo nuovo comando personalizzato, in questo caso la finestra di dialogo al centro dello schermo che ti dà il **Hello World!** criteri.).

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono le nozioni di base sull'utilizzo dell'estensibilità di Visual Studio, ecco dove è possibile ottenere ulteriori informazioni:Now that you know the basics of working with Visual Studio Extensibility, here's where you can learn more:

* [Iniziare a sviluppare le estensioni](starting-to-develop-visual-studio-extensions.md) di Visual Studio : esempi, esercitazioni. e la pubblicazione dell'estensione
* [Novità di Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) - Nuove funzionalità di estendibilità in Visual Studio 2017
* [Novità di Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) - Nuove funzionalità di estensibilità in Visual Studio 2019
* [All'interno di Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) - Informazioni sui dettagli dell'estensibilità di Visual StudioInside the Visual Studio SDK - Learn the details of Visual Studio Extensibility
