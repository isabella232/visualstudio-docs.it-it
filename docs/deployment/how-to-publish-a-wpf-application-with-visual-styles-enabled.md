---
title: Pubblicare un'app WPF con stili di visualizzazione abilitati
description: Informazioni su come pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati, che consente di modificare l'aspetto dei controlli in base al tema scelto dall'utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e372d3163dcef84d76d77e54c66cf9f7c788e213
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349854"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Procedura: Pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati

Gli stili di visualizzazione consentono di modificare l'aspetto dei controlli comuni in base al tema scelto dall'utente. Per impostazione predefinita, gli stili di visualizzazione non sono abilitati per le applicazioni Windows Presentation Foundation (WPF), pertanto è necessario abilitarli manualmente. Tuttavia, l'abilitazione degli stili di visualizzazione per un'applicazione WPF e la pubblicazione della soluzione causa un errore. In questo argomento viene descritto come risolvere l'errore e il processo per la pubblicazione di un'applicazione WPF con gli stili di visualizzazione abilitati. Per altre informazioni sugli stili di visualizzazione, vedere [Cenni preliminari sugli stili visivi](/windows/desktop/Controls/visual-styles-overview). Per ulteriori informazioni sul messaggio di errore, vedere la pagina relativa alla [risoluzione di errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Per risolvere l'errore e pubblicare la soluzione, è necessario eseguire le attività seguenti:

- [Pubblicare la soluzione senza gli stili visivi abilitati](#publish-the-solution-without-visual-styles-enabled).

- [Creare un file manifesto](#create-a-manifest-file).

- [Incorporare il file manifesto nel file eseguibile della soluzione pubblicata](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).

- [Firmare i manifesti dell'applicazione e della distribuzione](#sign-the-application-and-deployment-manifests).

  Quindi, è possibile spostare i file pubblicati nel percorso da cui si desidera che gli utenti finali installino l'applicazione.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Pubblica la soluzione senza gli stili di visualizzazione abilitata

1. Verificare che nel progetto non siano abilitati gli stili di visualizzazione. Per prima cosa, controllare il file manifesto del progetto per il codice XML seguente. Quindi, se il codice XML è presente, racchiudere il codice XML con un tag di commento.

     Per impostazione predefinita, gli stili di visualizzazione non sono abilitati.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Nelle procedure riportate di seguito viene illustrato come aprire il file manifesto associato al progetto.

    **Per aprire il file manifesto in un progetto Visual Basic**

    1. Nella barra dei menu scegliere **progetto** , proprietà *NomeProgetto* **Properties** , dove *NomeProgetto* è il nome del progetto WPF.

         Verranno visualizzate le pagine delle proprietà per il progetto WPF.

    2. Nella scheda **applicazione** scegliere **Visualizza impostazioni di Windows**.

         Il file app. manifest verrà aperto nell' **editor di codice**.

    **Per aprire il file manifesto in un progetto C#**

    1. Nella barra dei menu scegliere **progetto** , proprietà *NomeProgetto* **Properties** , dove *NomeProgetto* è il nome del progetto WPF.

         Verranno visualizzate le pagine delle proprietà per il progetto WPF.

    2. Nella scheda **applicazione** prendere nota del nome visualizzato nel campo manifesto. Si tratta del nome del manifesto associato al progetto.

        > [!NOTE]
        > Se il manifesto di **incorporamento con le impostazioni predefinite** o **Crea applicazione senza manifesto** viene visualizzato nel campo manifesto, gli stili di visualizzazione non sono abilitati. Se il nome di un file manifesto viene visualizzato nel campo manifesto, procedere con il passaggio successivo di questa procedura.

    3. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

         Questo pulsante Mostra tutti gli elementi del progetto, inclusi quelli che sono stati esclusi e quelli normalmente nascosti. Il file manifesto viene visualizzato come elemento di progetto.

2. Compilare e pubblicare la soluzione. Per altre informazioni su come pubblicare la soluzione, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>Creazione di un file manifesto

1. Incollare il codice XML seguente in un file del blocco note.

     Questo XML descrive l'assembly contenente i controlli che supportano gli stili di visualizzazione.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. In Blocco note, fare clic su **File** , quindi fare clic su **Salva con nome**.

3. Nella finestra di dialogo **Salva con nome** selezionare **tutti i file** nell'elenco a discesa **Salva come tipo** .

4. Nella casella **nome file** assegnare un nome al file e aggiungere *. manifest* alla fine del nome del file. Ad esempio: *Themes. manifest*.

5. Scegliere il pulsante **Sfoglia cartelle** , selezionare una cartella e quindi fare clic su **Salva**.

    > [!NOTE]
    > Le procedure rimanenti presuppongono che il nome del file sia *Themes. manifest* e che il file venga salvato nella directory *C:\Temp* del computer.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Incorporare il file manifesto nel file eseguibile della soluzione pubblicata

1. Aprire il **prompt dei comandi di Visual Studio**.

    Per ulteriori informazioni su come aprire il **prompt dei comandi di Visual Studio** , vedere [prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs).

   > [!NOTE]
   > I passaggi rimanenti fanno i presupposti seguenti sulla soluzione:
   >
   > - Il nome della soluzione è **MyWPFProject**.
   > - La soluzione si trova nella seguente directory: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - La soluzione viene pubblicata nella seguente directory: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - La versione più recente dei file dell'applicazione pubblicata si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Non è necessario usare il nome o i percorsi della directory descritti in precedenza. Il nome e i percorsi descritti in precedenza vengono usati solo per illustrare i passaggi necessari per la pubblicazione della soluzione.

2. Al prompt dei comandi, modificare il percorso della directory che contiene la versione più recente dei file dell'applicazione pubblicata. Nell'esempio seguente viene illustrato questo passaggio.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Al prompt dei comandi eseguire il comando seguente per incorporare il file manifesto nel file eseguibile dell'applicazione.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Firmare i manifesti dell'applicazione e della distribuzione

1. Al prompt dei comandi eseguire il comando seguente per rimuovere l'estensione *. deploy* dal file eseguibile nella directory corrente.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > In questo esempio si presuppone che solo un file abbia l'estensione di file *deploy* . Assicurarsi di rinominare tutti i file in questa directory che dispongono dell'estensione di file *. deploy* .

2. Al prompt dei comandi eseguire il comando seguente per firmare il manifesto dell'applicazione.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Questo esempio si basa sul presupposto che si firmi il manifesto usando il file con *estensione pfx* del progetto. Se non si firma il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firma il manifesto con un certificato che richiede una password, specificare l' `-password` opzione ( `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ).

3. Al prompt dei comandi, eseguire il comando seguente per aggiungere l'estensione *. deploy* al nome del file che è stato rinominato in un passaggio precedente di questa procedura.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > In questo esempio si presuppone che solo un file disponga di un'estensione di file *. deploy* . Assicurarsi di rinominare tutti i file in questa directory che in precedenza avevano l'estensione di file *. deploy* .

4. Al prompt dei comandi, eseguire il comando seguente per firmare il manifesto della distribuzione.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Questo esempio si basa sul presupposto che si firmi il manifesto usando il file con *estensione pfx* del progetto. Se non si firma il manifesto, è possibile omettere il `-cf` parametro utilizzato in questo esempio. Se si firma il manifesto con un certificato che richiede una password, specificare l' `-password` opzione, come nell'esempio seguente: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Dopo aver eseguito questi passaggi, è possibile spostare i file pubblicati nel percorso da cui si desidera che gli utenti finali possano installare l'applicazione. Se si intende aggiornare spesso la soluzione, è possibile spostare questi comandi in uno script ed eseguire lo script ogni volta che si pubblica una nuova versione.

## <a name="see-also"></a>Vedere anche

-[Risoluzione di errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Panoramica degli stili di visualizzazione](/windows/desktop/Controls/visual-styles-overview)
- [Abilitazione degli stili di visualizzazione](/windows/desktop/Controls/cookbook-overview)
- [Prompt dei comandi](/dotnet/framework/tools/developer-command-prompt-for-vs)
