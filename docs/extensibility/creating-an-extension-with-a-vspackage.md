---
title: Creazione di un'estensione con un pacchetto VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b66aef72d9af1ef40a061d1a82d18161a416586
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345352"
---
# <a name="create-an-extension-with-a-vspackage"></a>Creare un'estensione con un pacchetto VSPackage

Questa procedura dettagliata illustra come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Si userà il pacchetto VSPackage per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

1. Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** dialogo eseguendo una ricerca per "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento di pacchetto di Visual Studio denominato **FirstPackage**. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c#**  > **Extensibility** e selezionare **pacchetto di Visual Studio**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da *FirstPackage.cs*.

3. Compilare il progetto e avviare il debug.

    Viene visualizzata l'istanza sperimentale di Visual Studio. Per altre informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale, aprire il **degli strumenti** > **estensioni e aggiornamenti** finestra. Dovrebbero vedere le **FirstPackage** estensione qui. (Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**).

## <a name="load-the-vspackage"></a>Caricare il pacchetto VSPackage

A questo punto, l'estensione non viene caricato perché non c'è nulla che causa il caricamento. In genere, è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (scelta di un comando di menu, aprire una finestra degli strumenti), oppure specificando che il VSPackage verrà caricato in un contesto dell'interfaccia utente specifico. Per altre informazioni sul caricamento dei contesti di pacchetti VSPackage e l'interfaccia utente, vedere [caricamento di VSPackage](../extensibility/loading-vspackages.md). Per questa procedura, mostreremo come caricare un pacchetto VSPackage quando è aperta una soluzione.

1. Aprire il *FirstPackage.cs* file. Cerca la dichiarazione del `FirstPackage` classe. Sostituire gli attributi esistenti con gli attributi seguenti:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Ora si aggiungerà un messaggio che ci consente di sapere che ha caricato il pacchetto VSPackage. Viene usato il pacchetto VSPackage `Initialize()` dei servizi a tale scopo, in quanto è possibile ottenere Visual Studio solo dopo che il pacchetto VSPackage è stato individuato. (Per altre informazioni su come ottenere i servizi, vedere [come: Ottenere un servizio](../extensibility/how-to-get-a-service.md).) Sostituire il `Initialize()` metodo di `FirstPackage` con il codice che ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> del servizio, ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e le chiamate relative <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> (metodo).

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

4. Aprire una soluzione nell'istanza sperimentale. Si dovrebbe essere una finestra di messaggio con la dicitura **Initialize () all'interno del pacchetto prima**.
