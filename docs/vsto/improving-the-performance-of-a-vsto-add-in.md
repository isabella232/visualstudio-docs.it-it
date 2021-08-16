---
title: Migliorare le prestazioni di VSTO componente aggiuntivo
description: Informazioni su come ottimizzare VSTO componenti aggiuntivi creati per le applicazioni Office in modo che si abilitino, arrestino, abilitino ed eservitino rapidamente altre attività.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 669e690059acb6854eceee224b5439e07c08072d26ba08b3aa69c7fab0a8fe0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267728"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Migliorare le prestazioni di VSTO componente aggiuntivo
  È possibile offrire agli utenti un'esperienza migliore ottimizzando i componenti aggiuntivi VSTO creati per le applicazioni di Office per poterli avviare rapidamente, interromperli o usarli per aprire gli elementi ed eseguire altre attività. Se il componente aggiuntivo VSTO è per Outlook, è anche possibile ridurre la probabilità che il componente aggiuntivo VSTO venga disabilitato a causa delle prestazioni ridotte. È possibile incrementare le prestazioni del componente aggiuntivo VSTO implementando le strategie seguenti:

- [Caricare componenti aggiuntivi VSTO su richiesta](#Load).

- [Pubblicare soluzioni Office usando Windows Installer](#Publish).

- [Ignorare la reflection della barra multifunzione.](#Bypass)

- [Eseguire operazioni complesse in un thread di esecuzione separato](#Perform).

  Per altre informazioni su come ottimizzare un componente Outlook VSTO, vedere Criteri delle prestazioni per mantenere VSTO [componenti aggiuntivi abilitati.](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Caricare VSTO componenti aggiuntivi su richiesta
 È possibile configurare un componente aggiuntivo VSTO da caricare solo nelle circostanze seguenti:

- La prima volta che l'utente avvia l'applicazione dopo aver installato il componente aggiuntivo VSTO.

- La prima volta che l'utente interagisce con il componente aggiuntivo VSTO dopo l'avvio dell'applicazione in un qualsiasi momento successivo.

  Ad esempio, il VSTO aggiuntivo potrebbe popolare un foglio di lavoro con i dati quando l'utente sceglie un pulsante personalizzato con l'etichetta **Get My Data**. L'applicazione deve caricare il VSTO componente aggiuntivo almeno una  volta in modo che il pulsante Scarica dati personali possa essere visualizzato nella barra multifunzione. Tuttavia, il VSTO componente aggiuntivo non viene caricato di nuovo al successivo avvio dell'applicazione da parte dell'utente. Il componente aggiuntivo VSTO viene caricato solo quando l'utente seleziona il pulsante **Ottieni dati personali** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Per configurare una soluzione ClickOnce per caricare componenti aggiuntivi VSTO su richiesta

1. Scegliere il nodo di progetto in **Esplora soluzioni**.

2. Sulla barra dei menu scegliere **Visualizza pagine**  >  **delle proprietà.**

3. Nella scheda **Pubblica** scegliere il pulsante **Opzioni** .

4. Nella finestra di dialogo **Opzioni di pubblicazione** scegliere l'elemento elenco **Impostazioni Office** , selezionare l'opzione **Carica su richiesta** , quindi il pulsante **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Per configurare una soluzione Windows Installer per caricare componenti aggiuntivi VSTO su richiesta

1. Nel Registro di sistema impostare la voce della chiave `LoadBehavior` **_RADICE_\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _add-in ID_** su **0x10**.

     Per altre informazioni, vedere [Voci del Registro di sistema VSTO componenti aggiuntivi](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Per configurare una soluzione per caricare componenti aggiuntivi VSTO su richiesta durante il debug della soluzione

1. Creare uno script che imposta la voce della chiave `LoadBehavior` **_RADICE_\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _add-in ID_** su **0x10**.

     Nel codice seguente viene illustrato un esempio di questo script.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Creare un evento di post-compilazione in grado di aggiornare il Registro di sistema usando lo script.

     Nel codice seguente viene illustrato un esempio di una stringa di comando che è possibile aggiungere a un evento di post-compilazione.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Per informazioni su come creare un evento di post-compilazione in un progetto [C#, ](../ide/how-to-specify-build-events-csharp.md)vedere Procedura: Specificare eventi di compilazione &#40;C&#35;&#41;.

     Per informazioni su come creare un evento di post-compilazione in un progetto Visual Basic, vedere [Procedura: Specificare ](../ide/how-to-specify-build-events-visual-basic.md)eventi di compilazione &#40;Visual Basic&#41;.

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Pubblicare Office soluzioni usando Windows Installer
 Se si pubblica la soluzione usando il programma di installazione di Windows, il runtime di Visual Studio 2010 Tools per Office ignora i passaggi seguenti quando viene caricato il componente aggiuntivo VSTO.

- Convalida dello schema manifesto.

- Controllo automatico della disponibilità di aggiornamenti.

- Convalida della firma digitale dei manifesti della distribuzione.

  > [!NOTE]
  > Questo approccio non è necessario se si distribuisce VSTO componente aggiuntivo in una posizione sicura nei computer degli utenti.

  Per altre informazioni, vedere [Deploy an Office solution by using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Ignorare la reflection della barra multifunzione
 Se si compila una soluzione usando , assicurarsi che gli utenti abbia installato la versione più recente del runtime di Visual Studio 2010 Tools for Office quando si distribuisce la [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] soluzione. Le versioni precedenti del VSTO runtime si riflettono negli assembly della soluzione per individuare le personalizzazioni della barra multifunzione. Questo processo può rallentare il caricamento del componente aggiuntivo VSTO.

 In alternativa, è possibile impedire a qualsiasi versione del runtime di Visual Studio 2010 Tools per Office di usare la reflection per identificare le personalizzazioni della barra multifunzione. Per seguire questa strategia, eseguire l'override del `CreateRibbonExtensibility` metodo e restituire in modo esplicito gli oggetti della barra multifunzione. Se il VSTO non contiene personalizzazioni della barra multifunzione, restituire `null` all'interno del metodo .

 Nell'esempio seguente viene restituito un oggetto Ribbon basato sul valore di un campo .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs" id="Snippet1":::

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Eseguire operazioni dispendiose in un thread di esecuzione separato
 Si consiglia di eseguire le attività che richiedono tempo (ad esempio le attività a esecuzione prolungata, le connessioni di database o altri tipi di chiamate di rete) in un thread separato. Per altre informazioni, vedere [Supporto del threading in Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Tutto il codice che effettua chiamate nel modello a oggetti di Office deve essere eseguito nel thread principale.

## <a name="see-also"></a>Vedi anche

- [Caricamento su VSTO componenti aggiuntivi](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Caricamento ritardato di CLR nei componenti aggiuntivi di Office](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Creare componenti aggiuntivi VSTO per Office con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)