---
title: Estensione Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 04257a6ea4bfb3dbe788ba48ee3077b1847b000d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-isolated-shell"></a>Estensione Shell isolata
È possibile estendere la shell di Visual Studio isolated mediante l'aggiunta di un pacchetto VSPackage, un componente Managed Extensibility Framework (MEF) o un progetto VSIX generico per l'applicazione shell isolata.  
  
> [!NOTE]
>  I passaggi seguenti presuppongono l'esistenza di che è stata creata un'applicazione shell isolata di base utilizzando il modello di progetto Visual Studio Shell isolata. Per ulteriori informazioni su questo modello di progetto, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio si trova in tre posizioni diverse nella finestra di dialogo **Nuovo progetto** :  
  
1.  In **Visual Basic**, **estendibilità**. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  In **Visual c#**, **estendibilità**. Il linguaggio predefinito del progetto è C#.  
  
3.  In **altri tipi di progetto**, **estendibilità**. Il linguaggio predefinito del progetto è C++.  
  
## <a name="adding-a-vspackage"></a>Aggiunta di un pacchetto VSPackage  
 È possibile aggiungere un pacchetto VSPackage per l'applicazione shell isolata. La procedura seguente viene illustrato come creare uno che aggiunge i comandi di menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Per aggiungere un nuovo VSPackage  
  
1.  Aggiungere un progetto di pacchetto di Visual Studio denominato `MenuCommandsPackage`.  
  
2.  Nel **informazioni VSPackage di base** pagina della procedura guidata, impostare **nome società** a `Fabrikam` e **nome VSPackage** a `FabrikamMenuCommands`. Fare clic su **Avanti**.  
  
3.  Nella pagina successiva, selezionare **comando di Menu** e quindi scegliere **Avanti**.  
  
4.  Nella pagina successiva, impostare **nome comando** per `Fabrikam Command` e **ID di comando** a `cmdidFabrikamCommand`, quindi scegliere **Avanti**.  
  
5.  Nel **selezionare opzioni progetto Test** pagina, deselezionare le opzioni di test e quindi scegliere il **fine** pulsante.  
  
6.  Nel progetto ShellExtensionsVSIX, aprire il file vsixmanifest.  
  
     Il **asset** sezione deve contenere una voce per il progetto VSShellStub.AboutBoxPackage.  
  
7.  Scegliere il **New** pulsante.  
  
8.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare **Microsoft.VisualStudio.VsPackage**.  
  
9. Nel **origine** elenco, verificare che l'opzione **un progetto nella soluzione corrente** è selezionata. Nel **progetto** casella di riepilogo, seleziona **MenuCommandsPackage**.  
  
10. Salvare e chiudere il file.  
  
11. Ricompilare la soluzione e avviare il debug di shell isolata.  
  
12. Nella barra dei menu, scegliere **strumenti** menu, quindi **comando Fabrikam**.  
  
     Verrà visualizzata una finestra di messaggio.  
  
13. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-mef-component-part"></a>Aggiunta di un componente MEF  
 La procedura seguente viene illustrato come aggiungere un componente MEF all'applicazione shell isolata.  
  
#### <a name="to-add-a-mef-component"></a>Per aggiungere un componente MEF  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c#**, **estendibilità**, utilizzare il **Editor margine** modello per aggiungere un progetto. Assegnargli il nome `ShellEditorMargin`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Asset` , scegliere **aggiungere contenuto**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare **MEFComponent**.  
  
5.  Nel **origine** elenco, verificare che l'opzione **un progetto nella soluzione corrente** è selezionata. Nel **progetto** casella di riepilogo, seleziona **ShellEditorMargin**.  
  
6.  Salvare e chiudere il file.  
  
7.  Ricompilare la soluzione e avviare il debug di shell isolata.  
  
8.  Aprire un file di testo.  
  
     Un margine verde che contiene le parole "Hello world!" deve essere visualizzato nella parte inferiore della finestra di file di testo.  
  
9. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-generic-vsix-project"></a>Aggiunta di un progetto VSIX generico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Per aggiungere un progetto VSIX generico  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c#**, **estendibilità**, utilizzare il **VSIXProject** modello per aggiungere un progetto. Assegnargli il nome `EmptyVSIX`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file Source.extensions.vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Assets` , scegliere **New**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare il tipo di contenuto che si desidera aggiungere.  
  
5.  In **origine**, assicurarsi che il **un progetto nella soluzione corrente** opzione è selezionata. Nella casella di riepilogo, selezionare il nome del progetto VSIX.  
  
6.  Salvare e chiudere il file.  
  
7.  Se questo progetto include codice compilato, è necessario modificare il progetto in modo che l'assembly è incluso nell'output.  
  
    1.  Scaricare il progetto VSIX e aprire il file di progetto.  
  
    2.  Nel primo `<PropertyGroup>` bloccare, modificare il valore di `<CopyBuildOutputToOutputDirectory>` a `true`.  
  
    3.  Salvare e ricaricare il progetto.  
  
8.  Compilare ed eseguire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md)