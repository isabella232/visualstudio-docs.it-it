---
title: Estensione della shell isolata | Microsoft Docs
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
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839579"
---
# <a name="extending-the-isolated-shell"></a>Estensione della shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere la shell isolata di Visual Studio aggiungendo un pacchetto VSPackage, una parte del componente Managed Extensibility Framework (MEF) o un progetto VSIX generico all'applicazione shell isolata.  
  
> [!NOTE]
> I passaggi seguenti presuppongono che sia stata creata un'applicazione shell isolata di base usando il modello di progetto di Visual Studio Shell isolated. Per ulteriori informazioni su questo modello di progetto, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio si trova in tre posizioni diverse nella finestra di dialogo **Nuovo progetto** :  
  
1. In **Visual Basic** **estensibilità**. Il linguaggio predefinito del progetto è Visual Basic.  
  
2. In **Visual C#**, **estensibilità**. Il linguaggio predefinito del progetto è C#.  
  
3. In **altri tipi di progetto**, **estensibilità**. Il linguaggio predefinito del progetto è C++.  
  
## <a name="adding-a-vspackage"></a>Aggiunta di un pacchetto VSPackage  
 È possibile aggiungere un pacchetto VSPackage all'applicazione shell isolata. Nei passaggi seguenti viene illustrato come crearne uno che aggiunge i comandi di menu.  
  
#### <a name="to-add-a-new-vspackage"></a>Per aggiungere un nuovo pacchetto VSPackage  
  
1. Aggiungere un progetto di pacchetto di Visual Studio denominato `MenuCommandsPackage` .  
  
2. Nella pagina **informazioni VSPackage di base** della procedura guidata impostare **nome società** su `Fabrikam` e **nome VSPackage** su `FabrikamMenuCommands` . Fare clic su **Avanti**.  
  
3. Nella pagina successiva selezionare comando di **menu** , quindi fare clic su **Avanti**.  
  
4. Nella pagina successiva impostare **nome comando** su `Fabrikam Command` e **ID comando** su `cmdidFabrikamCommand` , quindi scegliere **Avanti**.  
  
5. Nella pagina **Seleziona opzioni progetto di test** deselezionare le opzioni di test, quindi scegliere il pulsante **fine** .  
  
6. Nel progetto ShellExtensionsVSIX aprire il file source. Extension. vsixmanifest.  
  
     La sezione **assets** deve contenere una voce per il progetto VSShellStub. AboutBoxPackage.  
  
7. Scegliere il pulsante **nuovo** .  
  
8. Nella finestra **Aggiungi nuovo asset** selezionare **Microsoft. VisualStudio. VSPackage**nell'elenco **tipo** .  
  
9. Nell'elenco **origine** verificare che sia selezionato **un progetto nella soluzione corrente** . Nella casella di riepilogo **progetto** selezionare **MenuCommandsPackage**.  
  
10. Salvare e chiudere il file.  
  
11. Ricompilare la soluzione e avviare il debug della shell isolata.  
  
12. Sulla barra dei menu scegliere strumenti dal menu **strumenti** e quindi **comando Fabrikam**.  
  
     Verrà visualizzata una finestra di messaggio.  
  
13. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-mef-component-part"></a>Aggiunta di una parte del componente MEF  
 Nei passaggi seguenti viene illustrato come aggiungere una parte del componente MEF all'applicazione shell isolata.  
  
#### <a name="to-add-a-mef-component"></a>Per aggiungere un componente MEF  
  
1. Nella finestra di dialogo **Aggiungi nuovo progetto** , in **Visual C#**, **estendibilità**, usare il modello di **margine dell'editor** per aggiungere un progetto. Denominarlo `ShellEditorMargin`.  
  
2. Nel progetto ShellExtensionsVSIX aprire il file source. Extension. vsixmanifest nella visualizzazione progettazione e non nella visualizzazione codice.  
  
3. Nella `Asset` sezione scegliere **Aggiungi contenuto**.  
  
4. Nell'elenco **tipo** della finestra **Aggiungi nuovo asset** selezionare **Microsoft. VisualStudio. MefComponent**.  
  
5. Nell'elenco **origine** verificare che sia selezionato **un progetto nella soluzione corrente** . Nella casella di riepilogo **progetto** selezionare **ShellEditorMargin**.  
  
6. Salvare e chiudere il file.  
  
7. Ricompilare la soluzione e avviare il debug della shell isolata.  
  
8. Aprire un file di testo.  
  
     Un margine verde che contiene le parole "Hello World!" deve essere visualizzato nella parte inferiore della finestra del file di testo.  
  
9. Arrestare il debug dell'applicazione.  
  
## <a name="adding-a-generic-vsix-project"></a>Aggiunta di un progetto VSIX generico  
  
#### <a name="to-add-a-generic-vsix-project"></a>Per aggiungere un progetto VSIX generico  
  
1. Nella finestra di dialogo **Aggiungi nuovo progetto** , in **Visual C#**, **estendibilità**, usare il modello **VSIXProject** per aggiungere un progetto. Denominarlo `EmptyVSIX`.  
  
2. Nel progetto ShellExtensionsVSIX aprire il file source. Extensions. vsixmanifest nella visualizzazione progettazione e non nella visualizzazione codice.  
  
3. Nella `Assets` sezione scegliere **nuovo**.  
  
4. Nell'elenco **tipo** della finestra **Aggiungi nuovo asset** selezionare il tipo di contenuto che si desidera aggiungere.  
  
5. In **origine**verificare che sia selezionata l'opzione **un progetto nella soluzione corrente** . Nella casella di riepilogo selezionare il nome del progetto VSIX.  
  
6. Salvare e chiudere il file.  
  
7. Se il progetto include codice compilato, è necessario modificare il progetto in modo che l'assembly venga incluso nell'output.  
  
    1. Scaricare il progetto VSIX e aprire il file di progetto.  
  
    2. Nel primo `<PropertyGroup>` blocco, modificare il valore di `<CopyBuildOutputToOutputDirectory>` in `true` .  
  
    3. Salvare e ricaricare il progetto.  
  
8. Compilare ed eseguire la soluzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
