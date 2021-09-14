---
title: 'Procedura: Specificare gli eventi di compilazione (C#)'
description: Informazioni su come usare gli eventi di compilazione per specificare i comandi che vengono eseguiti prima dell'inizio o al termine della compilazione.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e1ea031391b93d571b9f34ad820f1a6957dab242
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628781"
---
# <a name="how-to-specify-build-events-c"></a>Procedura: Specificare gli eventi di compilazione (C#)

È possibile usare gli eventi di compilazione per specificare i comandi da eseguire prima dell'inizio o al termine della compilazione. Gli eventi di compilazione vengono eseguiti solo se la compilazione raggiunge correttamente i punti corrispondenti nel processo di compilazione.

Quando un progetto viene compilato, gli eventi di pre-compilazione vengono aggiunti a un file denominato *PreBuildEvent.bat* e gli eventi di post-compilazione vengono aggiunti a un file denominato *PostBuildEvent.bat*. Per garantire il controllo degli errori, aggiungere comandi di controllo degli errori personalizzati alle istruzioni di compilazione.

## <a name="specify-a-build-event"></a>Specificare un evento di compilazione

1. In **Esplora soluzioni** selezionare il progetto per il quale si vuole specificare l'evento di compilazione.

2. Scegliere **Proprietà** dal menu **Progetto**.

3. Selezionare la scheda **Eventi di compilazione**.

4. Nella casella **Riga di comando eventi pre-compilazione** specificare la sintassi per l'evento di compilazione.

   > [!NOTE]
   > Gli eventi di pre-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata alcuna compilazione.

5. Nella casella **Riga di comando eventi post-compilazione** specificare la sintassi per l'evento di compilazione.

   > [!NOTE]
   > Aggiungere un'istruzione `call` prima di tutti i comandi di post-compilazione che eseguono file con estensione *bat*. Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

6. Nella casella **Esegui evento post-compilazione** specificare con quali condizioni eseguire l'evento di post-compilazione.

   > [!NOTE]
   > Per aggiungere una sintassi più lunga o per selezionare macro di compilazione dalla [finestra di dialogo Riga di comando eventi pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), fare clic sul pulsante con i puntini di sospensione (**...**) per visualizzare una casella di modifica.

   La sintassi dell'evento di compilazione può includere qualsiasi comando che sia valido in un prompt dei comandi o in un file con estensione *bat*. Perché vengano sicuramente eseguiti tutti i comandi successivi, il nome di un file batch deve essere preceduto da `call`.

   > [!NOTE]
   > Se l'evento di pre-compilazione o post-compilazione non viene completato correttamente, è possibile terminare la compilazione forzando l'azione dell'evento a uscire con un codice diverso da zero (0), che indica un esito positivo.

## <a name="example"></a>Esempio

La procedura seguente illustra come impostare la versione minima del sistema operativo nel manifesto dell'applicazione usando un comando *exe* chiamato da un evento di post-compilazione (il file *exe.manifest* nella directory del progetto). La versione minima del sistema operativo è un numero composto da quattro parti, ad esempio 4.10.0.0. Per impostare la versione minima del sistema operativo, il comando modifica la sezione `<dependentOS>` del manifesto:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Creare un comando exe per modificare il manifesto dell'applicazione

1. Creare un nuovo progetto **App console** per il comando. Assegnare al progetto il nome **ChangeOSVersionCS**.

2. In *Program.cs* aggiungere la riga seguente alle altre `using` direttive all'inizio del file:

   ```csharp
   using System.Xml;
   ```

3. Nello spazio dei nomi `ChangeOSVersionCS` sostituire l'implementazione della classe `Program` con il codice seguente:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   Il comando accetta due argomenti: il percorso del manifesto dell'applicazione, ovvero la cartella in cui il processo di compilazione crea il manifesto (in genere *Projectname.publish*), e la versione del nuovo sistema operativo.

4. Compilare il progetto.

5. Copiare il file con estensione *exe* in una directory, ad esempio *C:\TEMP\ChangeOSVersionVB.exe*.

Richiamare quindi questo comando in un evento di post-compilazione per modificare il manifesto dell'applicazione.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Richiamare un evento di post-compilazione per modificare il manifesto dell'applicazione

1. Creare un nuovo progetto **App Windows Forms** e denominarlo **CSWinApp**.

2. Con il progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

3. In **Creazione progetti**, individuare la pagina **Pubblica** e impostare **Posizione di pubblicazione** su *C:\TEMP*.

4. Pubblicare il progetto facendo clic su **Pubblica**.

   Il file manifesto viene compilato e salvato in *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Per visualizzare il manifesto, fare clic con il pulsante destro del mouse sul file, scegliere **Apri con**, selezionare **Seleziona il programma da un elenco** e quindi fare clic su **Blocco note**.

   Ricercare nel file l'elemento `<osVersionInfo>`. Ad esempio, la versione potrebbe essere:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. Tornare a **Creazione progetti**, fare clic sulla scheda **Eventi di compilazione** e quindi su **Modifica post-compilazione**.

6. Nella casella **Riga di comando eventi post-compilazione** immettere il comando seguente:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Quando si compila il progetto, questo comando imposta la versione minima del sistema operativo nel manifesto dell'applicazione su 5.1.2600.0.

   Poiché la macro `$(TargetPath)` esprime il percorso completo del file eseguibile in fase di creazione, `$(TargetPath).manifest` specifica il manifesto dell'applicazione creato nella directory *bin*. La pubblicazione copia questo manifesto nel percorso di pubblicazione impostato in precedenza.

7. Pubblicare nuovamente il progetto.

   Adesso la versione del manifesto dovrebbe essere:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Vedi anche

- [Pagina Eventi di compilazione, Project progettazione (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Finestra di dialogo riga di comando evento pre-compilazione/post-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Procedura: Specificare gli eventi di compilazione (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
