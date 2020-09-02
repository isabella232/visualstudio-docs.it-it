---
title: Creazione di un'estensione con un pacchetto VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197430"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Creazione di un'estensione con un pacchetto VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Il pacchetto VSPackage viene usato per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Creazione di un pacchetto VSPackage  
  
1. Creare un progetto VSIX denominato **FirstPackage**. Il modello di progetto VSIX è reperibile nella finestra di dialogo **nuovo progetto** in **Visual C#/extensibility**.  
  
2. Quando si apre il progetto, aggiungere un modello di elemento del pacchetto di Visual Studio denominato **FirstPackage**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi/nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C#/extensibility** e selezionare **pacchetto di Visual Studio**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in **FirstPackage.cs**.  
  
3. Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4. Nell'istanza sperimentale aprire la finestra **strumenti/estensioni e aggiornamenti** . L'estensione **FirstPackage** dovrebbe essere visualizzata qui. (Se si aprono **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Caricamento del pacchetto VSPackage  
 A questo punto l'estensione non viene caricata, perché non è presente alcun elemento che ne provoca il caricamento. In genere è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente (facendo clic su un comando di menu, aprendo una finestra degli strumenti) o specificando che il pacchetto VSPackage deve essere caricato in un contesto dell'interfaccia utente specifico. Per altre informazioni sul caricamento di pacchetti VSPackage e contesti dell'interfaccia utente, vedere [caricamento di pacchetti VSPackage](../extensibility/loading-vspackages.md). Per questa procedura verrà illustrato come caricare un pacchetto VSPackage quando una soluzione è aperta.  
  
1. Aprire il file FirstPackage.cs. Cercare la dichiarazione della classe FirstPackage. Sostituire gli attributi esistenti con il codice seguente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. Aggiungere un messaggio che informa che il pacchetto VSPackage è stato caricato. Per eseguire questa operazione si usa il metodo Initialize () del pacchetto VSPackage, perché è possibile ottenere i servizi di Visual Studio solo dopo che il pacchetto VSPackage è stato sito. Per ulteriori informazioni su come ottenere i servizi, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md). Sostituire il metodo Initialize () di FirstPackage con il codice che ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, ottiene l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e chiama il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodo.  
  
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
