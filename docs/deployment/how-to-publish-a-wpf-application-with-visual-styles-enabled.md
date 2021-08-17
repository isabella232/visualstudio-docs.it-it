---
title: Pubblicare un'app WPF con gli stili di visualizzazione abilitati
description: Informazioni su come pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati, che consente di modificare l'aspetto dei controlli in base al tema scelto dall'utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b231fc6635b5c974898ee2cc85ce8a4a64318039
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127896"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Procedura: Pubblicare un'applicazione WPF con gli stili di visualizzazione abilitati

Gli stili di visualizzazione consentono di modificare l'aspetto dei controlli comuni in base al tema scelto dall'utente. Per impostazione predefinita, gli stili di visualizzazione non sono abilitati per Windows Presentation Foundation (WPF), pertanto è necessario abilitarli manualmente. Tuttavia, l'abilitazione degli stili di visualizzazione per un'applicazione WPF e la pubblicazione della soluzione causano un errore. Questo argomento descrive come risolvere questo errore e il processo di pubblicazione di un'applicazione WPF con gli stili di visualizzazione abilitati. Per altre informazioni sugli stili di visualizzazione, vedere [Panoramica degli stili di visualizzazione](/windows/desktop/Controls/visual-styles-overview). Per altre informazioni sul messaggio di errore, vedere [Risolvere gli errori specifici nelle](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)ClickOnce distribuzione .

 Per risolvere l'errore e pubblicare la soluzione, è necessario eseguire le attività seguenti:

- [Pubblicare la soluzione senza gli stili di visualizzazione abilitati.](#publish-the-solution-without-visual-styles-enabled)

- [Creare un file manifesto](#create-a-manifest-file).

- [Incorporare il file manifesto nel file eseguibile della soluzione pubblicata.](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)

- [Firmare i manifesti dell'applicazione e della distribuzione](#sign-the-application-and-deployment-manifests).

  È quindi possibile spostare i file pubblicati nel percorso da cui si vuole che gli utenti finali installino l'applicazione.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Pubblicare la soluzione senza gli stili di visualizzazione abilitati

1. Assicurarsi che nel progetto non siano abilitati gli stili di visualizzazione. Per prima cosa, controllare il file manifesto del progetto per il codice XML seguente. Quindi, se il codice XML è presente, racchiudere il codice XML con un tag di commento.

     Per impostazione predefinita, gli stili di visualizzazione non sono abilitati.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Le procedure seguenti illustrano come aprire il file manifesto associato al progetto.

    **Per aprire il file manifesto in un progetto Visual Basic**

    1. Sulla barra dei menu scegliere **Project** proprietà *ProjectName* **,** dove *NomeProgetto* è il nome del progetto WPF.

         Vengono visualizzate le pagine delle proprietà per il progetto WPF.

    2. Nella scheda **Applicazione** scegliere **Visualizza** Windows Impostazioni .

         Il file app.manifest viene aperto **nell'editor di codice**.

    **Per aprire il file manifesto in un progetto C#**

    1. Sulla barra dei menu scegliere **Project** proprietà *ProjectName* **,** dove *NomeProgetto* è il nome del progetto WPF.

         Vengono visualizzate le pagine delle proprietà per il progetto WPF.

    2. Nella scheda **Applicazione** prendere nota del nome visualizzato nel campo manifesto. Nome del manifesto associato al progetto.

        > [!NOTE]
        > Se **nel campo Manifesto viene** visualizzato Incorpora manifesto con impostazioni predefinite o Crea applicazione senza **manifesto,** gli stili di visualizzazione non sono abilitati. Se il nome di un file manifesto viene visualizzato nel campo manifesto, procedere con il passaggio successivo di questa procedura.

    3. In **Esplora soluzioni** scegliere **Mostra tutti i file**.

         Questo pulsante mostra tutti gli elementi del progetto, inclusi quelli esclusi e quelli normalmente nascosti. Il file manifesto viene visualizzato come elemento di progetto.

2. Compilare e pubblicare la soluzione. Per altre informazioni su come pubblicare la soluzione, vedere [Procedura:](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)Pubblicare un'applicazione ClickOnce tramite la Pubblicazione guidata .

## <a name="create-a-manifest-file"></a>Creare un file manifesto

1. Incollare il codice XML seguente in un Blocco note file.

     Questo codice XML descrive l'assembly che contiene i controlli che supportano gli stili di visualizzazione.

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

2. In Blocco note, fare clic su **File**, quindi fare clic su **Salva con nome**.

3. **Nell'elenco a** discesa Tipo  file della finestra di dialogo Salva con nome selezionare Tutti **i file**.

4. Nella casella **Nome file** assegnare un nome al file e aggiungere *manifest* alla fine del nome file. Ad esempio: *themes.manifest*.

5. Scegliere il **pulsante Sfoglia cartelle** , selezionare una cartella e quindi fare clic su **Salva**.

    > [!NOTE]
    > Le procedure rimanenti presuppongono che il nome di questo file sia *themes.manifest* e che il file sia salvato nella directory *C:\temp* nel computer.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Incorporare il file manifesto nel file eseguibile della soluzione pubblicata

1. Aprire **Prompt dei comandi per gli sviluppatori per Visual Studio**.

    Per altre informazioni su come aprire Prompt dei comandi per gli sviluppatori per Visual Studio, vedere [Prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori.](../ide/reference/command-prompt-powershell.md)

   > [!NOTE]
   > I passaggi rimanenti fanno i presupposti seguenti sulla soluzione:
   >
   > - Il nome della soluzione è **MyWPFProject.**
   > - La soluzione si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - La soluzione viene pubblicata nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - La versione più recente dei file dell'applicazione pubblicata si trova nella directory seguente: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Non è necessario usare il nome o i percorsi della directory descritti in precedenza. Il nome e i percorsi descritti in precedenza vengono usati solo per illustrare i passaggi necessari per pubblicare la soluzione.

2. Al prompt dei comandi modificare il percorso della directory che contiene la versione più recente dei file dell'applicazione pubblicati. L'esempio seguente illustra questo passaggio.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Al prompt dei comandi eseguire il comando seguente per incorporare il file manifesto nel file eseguibile dell'applicazione.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Firmare i manifesti dell'applicazione e della distribuzione

1. Al prompt dei comandi eseguire il comando seguente per rimuovere l'estensione *deploy* dal file eseguibile nella directory corrente.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > In questo esempio si presuppone che un solo file abbia *l'estensione deploy.* Assicurarsi di rinominare tutti i file in questa directory con estensione *deploy.*

2. Al prompt dei comandi eseguire il comando seguente per firmare il manifesto dell'applicazione.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In questo esempio si presuppone che il manifesto sia stato firmato usando il file *con estensione pfx* del progetto. Se non si firma il manifesto, è possibile omettere il parametro `-cf` usato in questo esempio. Se si firma il manifesto con un certificato che richiede una password, specificare `-password` l'opzione ( `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ).

3. Al prompt dei comandi eseguire il comando seguente per aggiungere l'estensione *deploy* al nome del file rinominato in un passaggio precedente di questa procedura.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > In questo esempio si presuppone che un solo file sia con estensione *deploy.* Assicurarsi di rinominare tutti i file in questa directory che in precedenza avevano l'estensione *deploy.*

4. Al prompt dei comandi eseguire il comando seguente per firmare il manifesto della distribuzione.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In questo esempio si presuppone che il manifesto sia stato firmato usando il file *con estensione pfx* del progetto. Se non si firma il manifesto, è possibile omettere il parametro `-cf` usato in questo esempio. Se si firma il manifesto con un certificato che richiede una password, specificare l'opzione , come `-password` in questo esempio: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Dopo aver eseguito questi passaggi, è possibile spostare i file pubblicati nel percorso da cui si vuole che gli utenti finali installino l'applicazione. Se si intende aggiornare spesso la soluzione, è possibile spostare questi comandi in uno script ed eseguirlo ogni volta che si pubblica una nuova versione.

## <a name="see-also"></a>Vedi anche

- [Risoluzione di errori specifici nelle distribuzioni ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Panoramica degli stili di visualizzazione](/windows/desktop/Controls/visual-styles-overview)
- [Abilitazione degli stili di visualizzazione](/windows/desktop/Controls/cookbook-overview)
- [Prompt dei comandi per gli sviluppatori PowerShell per sviluppatori](../ide/reference/command-prompt-powershell.md)
