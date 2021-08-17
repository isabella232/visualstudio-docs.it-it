---
title: Hello World'esercitazione sull'estensione | Microsoft Docs
description: Informazioni su come aggiungere un nuovo comando come estensione Visual Studio, che prevede la creazione di un progetto, l'aggiunta di un comando e la modifica del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c53e0312de7d687c761546c0d5bd5d125665744fd6b78b71531a2eff749950f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376957"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Esercitazione: Creare la prima estensione: Hello World

Questo Hello World di esempio illustra come creare la prima estensione per Visual Studio. Questa esercitazione illustra come aggiungere un nuovo comando a Visual Studio.

Nel processo si apprenderà come:

* **[Creare un progetto di estendibilità](#create-an-extensibility-project)**
* **[Aggiungere un comando personalizzato](#add-a-custom-command)**
* **[Modificare il codice sorgente](#modify-the-source-code)**
* **[Eseguire](#run-it)**

Per questo esempio si userà Visual C# per aggiungere un pulsante di menu personalizzato denominato "Say Hello World!" simile al seguente:

![Hello World comando](media/hello-world-say-hello-world.png)

> [!NOTE]
> Questo articolo si applica Visual Studio in Windows. Per Visual Studio per Mac, vedere [Procedura dettagliata sull'estendibilità in Visual Studio per Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, assicurarsi di  aver installato il carico di lavoro di sviluppo dell'estensione Visual Studio, che include il modello VSIX necessario e il codice di esempio.

> [!NOTE]
> È possibile usare qualsiasi edizione di Visual Studio (Community, Professional o Enterprise) per creare un progetto Visual Studio estendibilità.

## <a name="create-an-extensibility-project"></a>Creare un progetto di estendibilità

::: moniker range="vs-2017"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**.

Passaggio 2. Nella casella di ricerca in alto a destra digitare "vsix" e selezionare visual C# **VSIX Project**. Immettere "HelloWorld" come **Nome** nella parte inferiore della finestra di dialogo e selezionare **OK.**

![nuovo progetto](media/hello-world-new-project.png)

Verrà ora visualizzata la pagina Attività iniziali e alcune risorse di esempio.

Se è necessario uscire da questa esercitazione e tornare a questa esercitazione, è possibile trovare il nuovo progetto HelloWorld nella **pagina iniziale** nella **sezione** Recenti.

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. Scegliere **Nuovo** > **Progetto** dal menu **File**. Cercare "vsix" e selezionare visual C# **VSIX Project** e quindi **Avanti**.

Passaggio 2. Immettere "HelloWorld" come nome **Project e** selezionare **Crea**.

![nuovo progetto](media/hello-world-new-project-2019.png)

Verrà ora visualizzato il progetto HelloWorld in **Esplora soluzioni**.

::: moniker-end

## <a name="add-a-custom-command"></a>Aggiungere un comando personalizzato

Passaggio 1. Se si seleziona il file *manifesto vsixmanifest,* è possibile visualizzare le opzioni modificabili, ad esempio descrizione, autore e versione.

Passaggio 2. Fare clic con il pulsante destro del mouse sul progetto (non sulla soluzione). Scegliere Aggiungi dal menu di scelta **rapida** e quindi **Nuovo elemento**.

Passaggio 3. Selezionare la **sezione Estendibilità** e quindi scegliere **Comando**.

Passaggio 4. Nel campo **Nome** nella parte inferiore immettere un nome file, ad esempio *Command.cs.*

![comando personalizzato](media/hello-world-vsix-command.png)

Il nuovo file di comando è visibile in **Esplora soluzioni**. Nel **nodo Risorse** sono disponibili altri file correlati al comando. Ad esempio, se si vuole modificare l'immagine, il file PNG è qui.

## <a name="modify-the-source-code"></a>Modificare il codice sorgente

A questo punto, il comando e il testo del pulsante vengono rigenerati automaticamente e non sono molto interessanti. È possibile modificare il file VSCT e il file CS se si desidera apportare modifiche.

* Il file VSCT è il percorso in cui è possibile rinominare i comandi, nonché definire la posizione in cui si Visual Studio comando. Quando si esplora il file VSCT, si noteranno commenti che illustrano le sezioni dei controlli del codice VSCT.

* Il file CS consente di definire azioni, ad esempio il gestore clic.

::: moniker range="vs-2017"

Passaggio 1. In **Esplora soluzioni** trovare il file VSCT per il nuovo comando. In questo caso, verrà chiamato *CommandPackage.vsct*.

![pacchetto di comandi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Passaggio 1. In **Esplora soluzioni** trovare il file VSCT per il pacchetto vs estensione. In questo caso, verrà chiamato *HelloWorldPackage.vsct.*

::: moniker-end

Passaggio 2. Modificare il `ButtonText` parametro in `Say Hello World!` .

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

Passaggio 3. Tornare a **Esplora soluzioni** trovare il file *Command.cs.* Nel metodo `Execute` modificare la stringa da a `message` `string.Format(..)` `Hello World!` .

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

Assicurarsi di salvare le modifiche in ogni file.

## <a name="run-it"></a>Eseguire

È ora possibile eseguire il codice sorgente nell'Visual Studio sperimentale.

Passaggio 1. Premere **F5** per eseguire il **comando Avvia** debug. Questo comando compila il progetto e avvia il debugger, avviando una nuova istanza di Visual Studio denominata **Istanza sperimentale**.

::: moniker range="vs-2017"

Le parole Istanza **sperimentale** verranno visualizzati nella barra Visual Studio del titolo.

![Barra del titolo dell'istanza sperimentale](media/hello-world-exp-instance.png)

::: moniker-end

Passaggio 2. Scegliere **Say Hello World!** dal menu Strumenti di **Istanza** **sperimentale.**

![risultato finale](media/hello-world-final-result.png)

Dovrebbe essere visualizzato l'output del nuovo **comando personalizzato,** in questo caso la finestra di dialogo al centro della schermata che fornisce la Hello World! .

## <a name="next-steps"></a>Passaggi successivi

Ora che si conoscono le nozioni di base sull'uso Visual Studio estendibilità, ecco dove è possibile ottenere altre informazioni:

* [Iniziare a sviluppare Visual Studio estensioni -](starting-to-develop-visual-studio-extensions.md) Esempi, esercitazioni. e pubblicazione dell'estensione
* [Novità di Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) - Nuove funzionalità di estendibilità in Visual Studio 2017
* [Novità di Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) - Nuove funzionalità di estendibilità in Visual Studio 2019
* [All'interno Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) - Informazioni dettagliate sull'Visual Studio estendibilità
