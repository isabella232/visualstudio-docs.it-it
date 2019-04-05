---
title: Estensione della Shell isolata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af64fa948754350eb1beb0f70dbac33981b595f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968541"
---
# <a name="extending-the-isolated-shell"></a>Estensione della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere la shell isolata di Visual Studio mediante l'aggiunta di un pacchetto VSPackage, una parte di componente Managed Extensibility Framework (MEF) o un progetto VSIX generico all'applicazione shell isolata.  
  
> [!NOTE]
>  I passaggi seguenti presuppongono l'esistenza di che è stata creata un'applicazione shell isolata di base usando il modello di progetto di Visual Studio Shell isolata. Per altre informazioni su questo modello di progetto, vedere [procedura dettagliata: Creazione di una semplice applicazione Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio si trova in tre posizioni diverse nella finestra di dialogo **Nuovo progetto** :  
  
1.  Sotto **Visual Basic**, **estendibilità**. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  Sotto **Visual c#**, **estendibilità**. Il linguaggio predefinito del progetto è C#.  
  
3.  Sotto **altri tipi di progetto**, **estendibilità**. Il linguaggio predefinito del progetto è C++.  
  
## <a name="adding-a-vspackage"></a>Aggiunta di un pacchetto VSPackage  
 È possibile aggiungere un pacchetto VSPackage all'applicazione shell isolata. La procedura seguente viene illustrato come crearne uno che aggiunge i comandi di menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Per aggiungere un nuovo pacchetto di Visual Studio  
  
1.  Aggiungere un progetto di pacchetto di Visual Studio denominato `MenuCommandsPackage`.  
  
2.  Nel **informazioni VSPackage di base** pagina della procedura guidata, impostare **nome società** al `Fabrikam` e **nome VSPackage** a `FabrikamMenuCommands`. Fare clic su **Avanti**.  
  
3.  Nella pagina successiva, selezionare **comando del Menu** e quindi scegliere **successivo**.  
  
4.  Nella pagina successiva, impostare **nome del comando** a `Fabrikam Command` e **ID comando** alla `cmdidFabrikamCommand`e quindi scegliere **Avanti**.  
  
5.  Nel **selezionare le opzioni del progetto di Test** pagina, deselezionare le opzioni di test e quindi scegliere il **fine** pulsante.  
  
6.  Nel progetto ShellExtensionsVSIX, aprire il file vsixmanifest.  
  
     Il **asset** sezione deve contenere una voce per il progetto VSShellStub.AboutBoxPackage.  
  
7.  Scegliere il **New** pulsante.  
  
8.  Nel **Aggiungi nuovo Asset** finestra, nelle **tipo** elenco, selezionare **Microsoft.VisualStudio.VsPackage**.  
  
9. Nel **origine** elenco, assicurarsi che **un progetto nella soluzione corrente** sia selezionata. Nel **Project** casella di riepilogo, seleziona **MenuCommandsPackage**.  
  
10. Salvare e chiudere il file.  
  
11. Ricompilare la soluzione e avviare il debug della shell isolata.  
  
12. Nella barra dei menu, scegliere **degli strumenti** menu, quindi **Fabrikam comando**.  
  
     Verrà visualizzata una finestra di messaggio.  
  
13. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-mef-component-part"></a>Aggiunta di una parte del componente MEF  
 I passaggi seguenti illustrano come aggiungere una parte del componente MEF all'applicazione shell isolata.  
  
#### <a name="to-add-a-mef-component"></a>Per aggiungere un componente MEF  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c#**, **estendibilità**, usare il **margine dell'Editor** modello per aggiungere un progetto. Assegnargli il nome `ShellEditorMargin`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Asset` keychains **Aggiungi contenuto**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nelle **tipo** elenco, selezionare **MEFComponent**.  
  
5.  Nel **origine** elenco, assicurarsi che **un progetto nella soluzione corrente** sia selezionata. Nel **Project** casella di riepilogo, seleziona **ShellEditorMargin**.  
  
6.  Salvare e chiudere il file.  
  
7.  Ricompilare la soluzione e avviare il debug della shell isolata.  
  
8.  Aprire un file di testo.  
  
     Un margine verde che contiene le parole "Hello world!" deve essere visualizzato nella parte inferiore della finestra di file di testo.  
  
9. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-generic-vsix-project"></a>Aggiunta di un progetto VSIX generico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Per aggiungere un progetto VSIX generico  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c#**, **estendibilità**, usare il **VSIXProject** modello per aggiungere un progetto. Assegnargli il nome `EmptyVSIX`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file Source.extensions.vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Assets` keychains **New**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nelle **tipo** elencare, selezionare il tipo di contenuto che si desidera aggiungere.  
  
5.  Nelle **origine**, assicurarsi che le **un progetto nella soluzione corrente** opzione è selezionata. Nella casella di riepilogo, selezionare il nome del progetto VSIX.  
  
6.  Salvare e chiudere il file.  
  
7.  Se questo progetto include codice compilato, è necessario modificare il progetto in modo che l'assembly è incluso nell'output.  
  
    1.  Scaricare il progetto VSIX e aprire il file di progetto.  
  
    2.  Nel primo `<PropertyGroup>` bloccare, modificare il valore di `<CopyBuildOutputToOutputDirectory>` a `true`.  
  
    3.  Salvare e ricaricare il progetto.  
  
8.  Compilare ed eseguire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
