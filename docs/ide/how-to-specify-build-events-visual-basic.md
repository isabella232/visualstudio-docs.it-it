---
title: 'Procedura: Specificare gli eventi di compilazione (Visual Basic)'
description: Informazioni su come gli eventi di Visual Basic possono essere usati per eseguire script, macro o altre azioni come parte del processo di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 272fa3bd66f863744986ed5dace44cf8327c08b02dd2e767ebff9e939cc19e65
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121318733"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Procedura: Specificare gli eventi di compilazione (Visual Basic)

Gli eventi di compilazione in Visual Basic possono essere usati per eseguire script, macro o altre azioni come parte del processo di compilazione. Gli eventi di pre-compilazione si verificano prima della compilazione e gli eventi di post-compilazione si verificano dopo la compilazione.

Gli eventi di compilazione vengono specificati nella finestra di dialogo **Eventi di compilazione** disponibile nella pagina **Compila** della **Creazione progetti**.

> [!NOTE]
> Visual Basic Express non supporta voci di eventi di compilazione. Questa caratteristica è supportata solo nel prodotto completo Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Come specificare eventi di pre e post-compilazione

### <a name="to-specify-a-build-event"></a>Per specificare un evento di compilazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Compila**.

3. Fare clic sul pulsante **Eventi di compilazione** per aprire la finestra di dialogo **Eventi di compilazione**.

4. Immettere gli argomenti della riga di comando per l'azione di pre-compilazione o post-compilazione e fare clic su **OK**.

    > [!NOTE]
    > Aggiungere un'istruzione `call` prima di tutti i comandi di post-compilazione che eseguono file con estensione *bat*. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Se l'evento di pre-compilazione o post-compilazione non viene completato correttamente, è possibile terminare la compilazione forzando l'azione dell'evento a uscire con un codice diverso da zero (0), che indica un esito positivo.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Esempio: come modificare le informazioni di un manifesto usando un evento di post-compilazione

La procedura seguente illustra come impostare la versione minima del sistema operativo nel manifesto dell'applicazione usando un comando *.exe* chiamato da un evento di post-compilazione (il file *.exe.manifest* nella directory del progetto). La versione minima del sistema operativo è un numero composto da quattro parti, ad esempio 4.10.0.0. A tale scopo, il comando modificherà la sezione `<dependentOS>` del manifesto:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Per creare un comando exe per modificare il manifesto dell'applicazione

1. Creare un'applicazione console per il comando. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

2. Nella finestra di dialogo **Nuovo progetto** nel nodo **Visual Basic** selezionare **Windows** e quindi scegliere il modello **Applicazione console**. Assegnare al progetto il nome `ChangeOSVersionVB`.

3. In *Module1.vb* aggiungere la riga seguente alle altre `Imports` istruzioni all'inizio del file:

   ```vb
   Imports System.Xml
   ```

4. Aggiungere il codice seguente a `Sub Main`:

   ```vb
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

   Il comando accetta due argomenti. Il primo argomento è il percorso del manifesto dell'applicazione, ovvero la cartella in cui il processo di compilazione crea il manifesto, in genere *\<ProjectName> .publish.* Il secondo argomento è la nuova versione del sistema operativo.

5. Nel menu **Compila** scegliere **Compila soluzione**.

6. Copiare il file con estensione *exe* in una directory, ad esempio *C:\TEMP\ChangeOSVersionVB.exe*.

   Successivamente, richiamare questo comando in un evento di post-compilazione per modificare il manifesto dell'applicazione.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Per richiamare un evento di post-compilazione per modificare il manifesto dell'applicazione

1. Creare un'applicazione Windows per il progetto da pubblicare. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

2. Nella finestra di dialogo **Nuovo progetto** del nodo **Visual Basic** selezionare **Desktop di Windows** e quindi scegliere il modello **App Windows Forms**. Assegnare al progetto il nome `VBWinApp`.
3. Con il progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

4. In **Creazione progetti**, passare alla pagina **Pubblica** e impostare **Posizione di pubblicazione** su *C:\TEMP*.

5. Pubblicare il progetto facendo clic su **Pubblica**.

     Il file manifesto verrà compilato e inserito in *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Per visualizzare il manifesto, fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**, fare clic su **Seleziona il programma da un elenco** e quindi scegliere **Blocco note**.

     Ricercare nel file l'elemento `<osVersionInfo>`. Ad esempio, la versione potrebbe essere:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. In **Creazione progetti**, passare alla scheda **Compila** e fare clic sul pulsante **Eventi di compilazione** per aprire la finestra di dialogo **Eventi di compilazione**.

7. Nella casella **Riga di comando eventi post-compilazione** immettere il comando seguente:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Quando si compila il progetto, questo comando imposterà la versione minima del sistema operativo nel manifesto dell'applicazione su 5.1.2600.0.

     La macro `$(TargetPath)` indica il percorso completo dell'eseguibile che si sta creando. Di conseguenza, *$(TargetPath).manifest* specificherà il manifesto dell'applicazione creato nella directory *bin*. La pubblicazione copierà questo manifesto nel percorso di pubblicazione impostato in precedenza.

8. Pubblicare nuovamente il progetto. Passare alla pagina **Pubblica** e fare clic su **Pubblica**.

     Visualizzare nuovamente il manifesto. Per visualizzare il manifesto, passare alla directory di pubblicazione, fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**, quindi fare clic su **Seleziona il programma da un elenco** e scegliere **Blocco note**.

     Adesso la versione dovrebbe essere:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Vedi anche

- [Pagina Compilazione, progettazione Project (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Pagina Pubblica, progettazione Project](../ide/reference/publish-page-project-designer.md)
- [Finestra di dialogo riga di comando evento pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Procedura: Specificare gli eventi di compilazione (C#)](../ide/how-to-specify-build-events-csharp.md)
