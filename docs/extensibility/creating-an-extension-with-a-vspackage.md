---
title: Creazione di un'estensione con un pacchetto VSPackage | Microsoft Docs
description: Informazioni su come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage usando il pacchetto VSPackage per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 29b7dd4a3cd6da6a13d999419bfef5a7eafa839adc53df115860e0785d534f75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293521"
---
# <a name="create-an-extension-with-a-vspackage"></a>Creare un'estensione con un vspackage

Questa procedura dettagliata illustra come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Il vspackage verrà utilizzato per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vspackage"></a>Creare un VSPackage

1. Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nella **finestra di dialogo Nuovo Project** ricerca di "vsix".

2. Quando si apre il progetto, aggiungere un modello di Visual Studio pacchetto denominato **FirstPackage**. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Nella finestra **di dialogo Aggiungi nuovo elemento** passare a Estendibilità di Visual **C#** e  >   selezionare Visual Studio **pacchetto**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in *FirstPackage.cs*.

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'Visual Studio sperimentale di . Per altre informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale aprire la **finestra Estensioni** e  >  **aggiornamenti degli** strumenti. Verrà visualizzata **l'estensione FirstPackage** qui. Se si aprono **estensioni e aggiornamenti nell'istanza** funzionante di Visual Studio, non verrà visualizzato **FirstPackage**.

## <a name="load-the-vspackage"></a>Caricare il pacchetto VSPackage

A questo punto, l'estensione non viene caricata perché non è presente alcun elemento che ne causa il caricamento. È in genere possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (facendo clic su un comando di menu, aprendo una finestra degli strumenti) o specificando che il pacchetto VSPackage deve essere caricato in un contesto dell'interfaccia utente specifico. Per altre informazioni sul caricamento di VSPackage e contesti dell'interfaccia utente, vedere [Caricamento di VSPackage](../extensibility/loading-vspackages.md). Per questa procedura, verrà illustrato come caricare un vspackage quando una soluzione è aperta.

1. Aprire il file *FirstPackage.cs.* Cercare la dichiarazione della `FirstPackage` classe . Sostituire gli attributi esistenti con gli attributi seguenti:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Aggiungere un messaggio che indica che il pacchetto VSPackage è stato caricato. A tale scopo, viene utilizzato il metodo di VSPackage, perché è possibile ottenere Visual Studio solo dopo il sito del `Initialize()` pacchetto VSPackage. Per altre informazioni sul recupero dei servizi, vedere [Procedura: Ottenere un servizio.](../extensibility/how-to-get-a-service.md) Sostituire il `Initialize()` metodo di con il codice che ottiene il `FirstPackage` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, ottiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> l'interfaccia e chiama il relativo metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> .

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

4. Aprire una soluzione nell'istanza sperimentale. Verrà visualizzata una finestra di messaggio con il messaggio First Package Inside Initialize() ( Primo **pacchetto all'interno di Initialize()).**
