---
title: Migliorare le prestazioni di un componente aggiuntivo VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc1605a61d63a5d314ae1f02d864124185546ada
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Migliorare le prestazioni di un componente aggiuntivo VSTO
  È possibile offrire agli utenti un'esperienza migliore ottimizzando i componenti aggiuntivi VSTO creati per le applicazioni di Office per poterli avviare rapidamente, interromperli o usarli per aprire gli elementi ed eseguire altre attività. Se il componente aggiuntivo VSTO è per Outlook, è anche possibile ridurre la probabilità che il componente aggiuntivo VSTO venga disabilitato a causa delle prestazioni ridotte. È possibile incrementare le prestazioni del componente aggiuntivo VSTO implementando le strategie seguenti:  
  
-   [Caricare componenti aggiuntivi VSTO su richiesta](#Load).  
  
-   [Pubblicare soluzioni Office usando Windows Installer](#Publish).  
  
-   [Disabilitare la reflection della barra multifunzione](#Bypass).  
  
-   [Eseguire operazioni complesse in un thread di esecuzione separato](#Perform).  
  
 Per ulteriori informazioni su come ottimizzare un componente aggiuntivo VSTO di Outlook, vedere [criteri delle prestazioni per mantenere i componenti aggiuntivi VSTO abilitati](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Caricare componenti aggiuntivi VSTO su richiesta  
 È possibile configurare un componente aggiuntivo VSTO da caricare solo nelle circostanze seguenti:  
  
-   La prima volta che l'utente avvia l'applicazione dopo aver installato il componente aggiuntivo VSTO.  
  
-   La prima volta che l'utente interagisce con il componente aggiuntivo VSTO dopo l'avvio dell'applicazione in un qualsiasi momento successivo.  
  
 Ad esempio, il componente aggiuntivo VSTO potrebbe popolare un foglio di lavoro con i dati quando l'utente sceglie un pulsante personalizzato con etichetta **Ottieni dati personali**. L'applicazione deve caricare il componente aggiuntivo VSTO almeno una volta in modo che il **Ottieni dati personali** pulsante può essere visualizzato nella barra multifunzione. Tuttavia, il componente aggiuntivo VSTO non viene caricato nuovamente quando l'utente avvia l'applicazione al successivo. Il componente aggiuntivo VSTO viene caricato solo quando l'utente seleziona il pulsante **Ottieni dati personali** .  
  
### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Per configurare una soluzione ClickOnce per caricare componenti aggiuntivi VSTO su richiesta  
  
1.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
2.  Sulla barra dei menu scegliere **Visualizza** > **Pagine delle proprietà**.  
  
3.  Nella scheda **Pubblica** scegliere il pulsante **Opzioni** .  
  
4.  Nella finestra di dialogo **Opzioni di pubblicazione** scegliere l'elemento elenco **Impostazioni Office** , selezionare l'opzione **Carica su richiesta** , quindi il pulsante **OK** .  
  
### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Per configurare una soluzione Windows Installer per caricare componenti aggiuntivi VSTO su richiesta  
  
1.  Nel Registro di sistema, impostare il `LoadBehavior` voce del **_radice_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID componente aggiuntivo_** chiave per **0x10**.  
  
     Per altre informazioni, vedere [voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Per configurare una soluzione per caricare componenti aggiuntivi VSTO su richiesta durante il debug della soluzione  
  
1.  Creare uno script che consente di impostare il `LoadBehavior` voce del **_radice_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID componente aggiuntivo_** chiave per **0x10**.  
  
     Nel codice seguente viene illustrato un esempio di questo script.  
  
    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Creare un evento di post-compilazione in grado di aggiornare il Registro di sistema usando lo script.  
  
     Nel codice seguente viene illustrato un esempio di una stringa di comando che è possibile aggiungere a un evento di post-compilazione.  
  
    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Per informazioni su come creare eventi di post-compilazione in un progetto c#, vedere [procedura: specificare eventi di compilazione &#40;C&#35;&#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Per informazioni su come creare un evento di post-compilazione in un progetto di Visual Basic, vedere [procedura: specificare eventi di compilazione &#40;Visual Basic&#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Pubblicare soluzioni Office tramite Windows Installer  
 Se si pubblica la soluzione tramite Windows Installer, Visual Studio 2010 Tools per Office runtime consente di ignorare i passaggi seguenti quando il componente aggiuntivo VSTO viene caricato.  
  
-   Convalida dello schema manifesto.  
  
-   Controllo automatico della disponibilità di aggiornamenti.  
  
-   Convalida della firma digitale dei manifesti della distribuzione.  
  
    > [!NOTE]  
    >  Questo approccio non è necessario se si distribuisce il componente aggiuntivo VSTO in una posizione sicura nei computer degli utenti.  
  
 Per altre informazioni, vedere [distribuire una soluzione Office tramite Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Disabilitare la reflection della barra multifunzione  
 Se si compila una soluzione utilizzando [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], assicurarsi che gli utenti abbiano installato la versione più recente di Visual Studio 2010 Tools per Office runtime quando si distribuisce la soluzione. Le versioni precedenti di quel runtime effettuavano la reflection negli assembly della soluzione per individuare le personalizzazioni della barra multifunzione. Questo processo può rallentare il caricamento del componente aggiuntivo VSTO.  
  
 In alternativa, è possibile impedire qualsiasi versione di Visual Studio 2010 Tools per Office runtime utilizzando la reflection per identificare le personalizzazioni della barra multifunzione. Per seguire questa strategia, eseguire l'override di `CreateRibbonExtensibility` metodo e restituito in modo esplicito gli oggetti della barra multifunzione. Se il componente aggiuntivo VSTO non contiene tutte le personalizzazioni della barra multifunzione, restituire `null` all'interno del metodo.  
  
 L'esempio seguente restituisce un oggetto della barra multifunzione in base al valore di un campo.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Eseguire operazioni complesse in un thread di esecuzione separato  
 Si consiglia di eseguire le attività che richiedono tempo (ad esempio le attività a esecuzione prolungata, le connessioni di database o altri tipi di chiamate di rete) in un thread separato. Per altre informazioni, vedere [supporto del Threading in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Tutto il codice che effettua chiamate nel modello a oggetti di Office deve essere eseguito nel thread principale.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti aggiuntivi VSTO di caricamento su richiesta](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Caricamento ritardato di CLR nei componenti aggiuntivi di Office](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [Prestazioni di VSTO: il caricamento ritardato e utente (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Miglioramenti delle prestazioni sarà presto disponibile a un service pack vicino utente (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [Prestazioni di VSTO: sulla barra multifunzione reflection (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  