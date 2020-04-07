---
title: Creazione di un'estensione con un pacchetto VSPackage . Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739533"
---
# <a name="create-an-extension-with-a-vspackage"></a>Creare un'estensione con un pacchetto VSPackageCreate an extension with a VSPackage

Questa procedura dettagliata viene illustrato come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage.This walkthrough shows you how to create a VSIX project and add a VSPackage project item. Useremo il pacchetto VSPackage per ottenere il servizio della shell dell'interfaccia utente per visualizzare una finestra di messaggio.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vspackage"></a>Creare un pacchetto VSPackageCreate a VSPackage

1. Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento del pacchetto di Visual Studio denominato **FirstPackage**. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Pacchetto di Visual Studio**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando *in FirstPackage.cs*.

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio appears. Per ulteriori informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale aprire la finestra**Estensioni e aggiornamenti** degli **strumenti.** >  Si dovrebbe vedere il **FirstPackage** estensione qui. Se si aprono **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**.

## <a name="load-the-vspackage"></a>Caricare il pacchetto VSPackageLoad the VSPackage

A questo punto, l'estensione non viene caricata perché non vi è nulla che ne determina il caricamento. In genere è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (facendo clic su un comando di menu, aprendo una finestra degli strumenti) o specificando che il pacchetto VSPackage deve essere caricato in un contesto dell'interfaccia utente specifico. Per ulteriori informazioni sul caricamento di PACCHETTIPackage e contesti dell'interfaccia utente, vedere [Caricamento di pacchetti VSPackage](../extensibility/loading-vspackages.md). Per questa procedura, verrà illustrato come caricare un pacchetto VSPackage quando una soluzione è aperta.

1. Aprire il file *di FirstPackage.cs.* Cercare la dichiarazione `FirstPackage` della classe. Sostituire gli attributi esistenti con i seguenti attributi:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Aggiungiamo un messaggio che ci fa sapere che il pacchetto VSPackage è stato caricato. Usiamo il metodo del `Initialize()` pacchetto VSPackage per fare questo, perché è possibile ottenere i servizi di Visual Studio solo dopo che il pacchetto VSPackage è stato individuato. Per ulteriori informazioni su come ottenere servizi, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md). Sostituire `Initialize()` il `FirstPackage` metodo di con <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> il codice <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> che ottiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> il servizio, ottiene l'interfaccia e chiama il relativo metodo.

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

4. Aprire una soluzione nell'istanza sperimentale. Verrà visualizzata una finestra di messaggio che indica **Primo pacchetto all'interno di Initialize()**.
