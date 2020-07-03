---
title: Creazione di un'estensione con un pacchetto VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68ade2f8d334c1f93349e396d910fa300f6b5417
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903857"
---
# <a name="create-an-extension-with-a-vspackage"></a>Creare un'estensione con un pacchetto VSPackage

Questa procedura dettagliata illustra come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Il pacchetto VSPackage viene usato per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

1. Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Quando si apre il progetto, aggiungere un modello di elemento del pacchetto di Visual Studio denominato **FirstPackage**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#**  >  **estensibilità** di Visual C# e selezionare **pacchetto di Visual Studio**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in *FirstPackage.cs*.

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale aprire la finestra **strumenti**  >  **estensioni e aggiornamenti** . L'estensione **FirstPackage** dovrebbe essere visualizzata qui. (Se si aprono **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**).

## <a name="load-the-vspackage"></a>Caricare il pacchetto VSPackage

A questo punto, l'estensione non viene caricata perché non sono presenti elementi che ne causano il caricamento. In genere è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (facendo clic su un comando di menu, aprendo una finestra degli strumenti) o specificando che il pacchetto VSPackage deve essere caricato in un contesto dell'interfaccia utente specifico. Per altre informazioni sul caricamento di pacchetti VSPackage e contesti dell'interfaccia utente, vedere [caricamento di pacchetti VSPackage](../extensibility/loading-vspackages.md). Per questa procedura verrà illustrato come caricare un pacchetto VSPackage quando una soluzione è aperta.

1. Aprire il file *FirstPackage.cs* . Cercare la dichiarazione della `FirstPackage` classe. Sostituire gli attributi esistenti con gli attributi seguenti:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Aggiungere un messaggio che informa che il pacchetto VSPackage è stato caricato. `Initialize()`Per eseguire questa operazione, viene usato il metodo del pacchetto VSPackage, perché è possibile ottenere i servizi di Visual Studio solo dopo che il pacchetto VSPackage è stato sito. Per ulteriori informazioni su come ottenere i servizi, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md). Sostituire il `Initialize()` metodo di `FirstPackage` con il codice che ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, ottiene l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e chiama il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodo.

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

4. Aprire una soluzione nell'istanza sperimentale. Verrà visualizzata una finestra di messaggio che indica il **primo pacchetto all'interno di Initialize ()**.
