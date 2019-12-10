---
title: Voci del registro di sistema per i componenti aggiuntivi VSTO
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 464820258e5c20474d74f92eb108344deccc49f1
ms.sourcegitcommit: 0a8855572c6c88f4b2ece232c04aa124fbd9cec3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955049"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Voci del registro di sistema per i componenti aggiuntivi VSTO
  È necessario creare un set specifico di voci del Registro di sistema quando si distribuiscono componenti aggiuntivi VSTO creati con Visual Studio. Queste voci del Registro di sistema forniscono informazioni che consentono all'applicazione di Microsoft Office di individuare e caricare il componente aggiuntivo VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Quando si compila il progetto, Visual Studio crea queste voci del Registro di sistema nel computer di sviluppo, in modo che sia possibile eseguire il componente aggiuntivo VSTO ed effettuarne il debug con facilità. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del registro di sistema vengono create automaticamente nel computer dell'utente finale. Se si usa Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del registro di sistema nel computer dell'utente finale.

 Per altre informazioni sull'uso delle voci del Registro di sistema durante il processo di caricamento per i componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> In questo argomento la dicitura *ID componente aggiuntivo* rappresenta l'identificatore univoco del componente aggiuntivo VSTO. Per impostazione predefinita, l'ID è il nome dell'assembly del componente aggiuntivo VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registra i componenti aggiuntivi VSTO per l'utente corrente e per tutti gli utenti
 Un componente aggiuntivo VSTO installato può essere registrato in due modi diversi:

- Solo per l'utente corrente (ovvero è disponibile solo per l'utente che ha eseguito l'accesso al computer quando è installato il componente aggiuntivo VSTO). In questo caso, le voci del registro di sistema vengono create nel **HKEY_CURRENT_USER**.

- Per tutti gli utenti (ovvero qualsiasi utente che accede al computer può usare il componente aggiuntivo VSTO). In questo caso, le voci del registro di sistema vengono create in **HKEY_LOCAL_MACHINE**.

  Tutti i componenti aggiuntivi VSTO creati con Visual Studio possono essere registrati per l'utente corrente. Tuttavia, i componenti aggiuntivi VSTO possono essere registrati per tutti gli utenti solo in determinati scenari. Questi scenari dipendono dalla versione di Microsoft Office installata nel computer e dal modo in cui è stato distribuito il componente aggiuntivo VSTO.

### <a name="deployment-type"></a>Tipo di distribuzione
 Se si usa ClickOnce per distribuire un componente aggiuntivo VSTO, quest'ultimo può essere registrato solo per l'utente corrente. Questo perché ClickOnce supporta solo la creazione di chiavi in **HKEY_CURRENT_USER**. Se si vuole registrare un componente aggiuntivo VSTO per tutti gli utenti di un computer, è necessario distribuirlo tramite Windows Installer. Per altre informazioni su questi tipi di distribuzione, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e [distribuire una soluzione Office usando Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Voci del Registro di sistema
 Le voci del registro di sistema del componente aggiuntivo VSTO obbligatorie si trovano nelle seguenti chiavi del registro di sistema in cui la *radice* è **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE** a seconda che l'installazione sia per l'utente corrente o per tutti gli utenti.

|Applicazione di Office|Percorso di configurazione|
|------------------|------------------|
|Visio|*Radice*\SOFTWARE\Microsoft\\*Visio*\Addins\\*ID componente aggiuntivo*|
|Tutti gli altri|*Radice*\Software\Microsoft\Office\\*nome dell'applicazione di Office*\Addins\\*ID componente aggiuntivo*|

> [!NOTE]
> Se il programma di installazione è destinato a tutti gli utenti in Windows a 64 bit, è consigliabile includere due voci del registro di sistema, una sotto la HKEY_LOCAL_MACHINE \Software\Microsoft e una nell'HKEY_LOCAL_MACHINE \SOFTWARE\\**Wow6432Node**\Microsoft hive. Questo perché è possibile che gli utenti usino le versioni di Office a 32 bit o a 64 bit nel computer.
>
>Se il programma di installazione è destinato all'utente corrente, non è necessario installarlo in WOW6432Node perché il percorso di \SOFTWARE HKEY_CURRENT_USER è condiviso.
>
>Per ulteriori informazioni, vedere la pagina relativa ai [dati delle applicazioni a 32 bit e a 64 bit nel registro di sistema.](https://docs.microsoft.com/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 Nella tabella seguente sono elencate le voci presenti in questa chiave del Registro di sistema.

|Voce|Tipo di|Valore|
|-----------|----------|-----------|
|**Descrizione**|REG_SZ|Richiesto. Breve descrizione del componente aggiuntivo VSTO.<br /><br /> Questa descrizione viene visualizzata quando l'utente seleziona il componente aggiuntivo VSTO nel riquadro **Componenti aggiuntivi** della finestra di dialogo **Opzioni** nell'applicazione di Microsoft Office.|
|**FriendlyName**|REG_SZ|Richiesto. Nome descrittivo del componente aggiuntivo VSTO visualizzato nella finestra di dialogo **Componenti aggiuntivi COM** dell'applicazione di Microsoft Office. Il valore predefinito è l'ID del componente aggiuntivo VSTO.|
|**LoadBehavior**|REG_DWORD|Richiesto. Valore che specifica quando l'applicazione tenta di caricare il componente aggiuntivo VSTO e lo stato corrente del componente aggiuntivo VSTO (caricato o scaricato).<br /><br /> Per impostazione predefinita, questo valore è impostato su 3, a indicare che il componente aggiuntivo VSTO viene caricato all'avvio. Per ulteriori informazioni, vedere [valori LoadBehavior](#LoadBehavior). **Nota:**  Se un utente disabilita il componente aggiuntivo VSTO, tale azione modifica il valore di **LoadBehavior** nell'hive del registro di sistema **HKEY_CURRENT_USER** . Per ogni utente, il valore del valore **LoadBehavior** nel HKEY_CURRENT_USER hive sostituisce il valore predefinito di **LoadBehavior** definito nel **HKEY_LOCAL_MACHINE** hive.|
|**Manifest**|REG_SZ|Richiesto. Percorso completo del manifesto della distribuzione del componente aggiuntivo VSTO. Può essere un percorso contenuto nel computer locale, una condivisione di rete (UNC) o un server Web (HTTP).<br /><br /> Se si usa Windows Installer per distribuire la soluzione, è necessario aggiungere il prefisso **file:///** al percorso di **manifesto** . È anche necessario aggiungere la stringa  **&#124;vstolocal** (ovvero il carattere **&#124;** barra verticale seguito da **vstolocal**) alla fine di questo percorso. Il suffisso garantisce che la soluzione venga caricata dalla cartella di installazione e non dalla cache ClickOnce. Per altre informazioni, vedere [distribuire una soluzione Office usando Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Nota:**  Quando si compila un componente aggiuntivo VSTO nel computer di sviluppo, Visual Studio aggiunge automaticamente la  **&#124;stringa vstolocal** a questa voce del registro di sistema.|

### <a name="OutlookEntries"></a>Voci del registro di sistema per le aree del modulo di Outlook
 Se si crea un'area del modulo personalizzata in un componente aggiuntivo VSTO per Outlook, vengono usate voci aggiuntive del Registro di sistema per registrare l'area con Outlook. Queste voci vengono create in una chiave del Registro di sistema diversa per ogni classe di messaggio supportata dall'area. Queste chiavi del registro di sistema si trovano nel percorso seguente, dove *root* è **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE**.

 \Software\Microsoft\Office\Outlook\FormRegions *radice*\\*classe messaggio*

 Analogamente alle altre voci del Registro di sistema condivise da tutti i componenti aggiuntivi VSTO, Visual Studio crea le voci relative all'area del modulo nel computer di sviluppo durante la compilazione del progetto. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del registro di sistema vengono create automaticamente nel computer dell'utente finale. Se si usa Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del registro di sistema nel computer dell'utente finale.

 Per ulteriori informazioni sulle voci del registro di sistema dell'area del modulo, vedere [specificare il percorso di un'area del modulo in un modulo personalizzato](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Per altre informazioni sulle aree del modulo di Outlook, vedere [creare aree del modulo di Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="LoadBehavior"></a>Valori LoadBehavior
 La voce **LoadBehavior** sotto il \Software\Microsoft\Office *radice*\\*nome dell'applicazione*\Addins\\chiave *ID componente aggiuntivo* contiene una combinazione bit per bit di valori che specificano il comportamento in fase di esecuzione del componente aggiuntivo VSTO. Il bit di ordine più basso (valori 0 e 1) indica se il componente aggiuntivo VSTO è attualmente caricato o scaricato. Gli altri bit indicano quando l'applicazione tenta di caricare il componente aggiuntivo VSTO.

 In genere, la voce **LoadBehavior** è destinata a essere impostata su 0, 3 o 16 (in decimale) quando il componente aggiuntivo VSTO viene installato nei computer degli utenti finali. Per impostazione predefinita, Visual Studio imposta la voce **LoadBehavior** del componente aggiuntivo VSTO su 3 quando questo viene compilato o pubblicato.

 Nella tabella seguente sono elencati tutti i valori possibili della voce **LoadBehavior** . Alcune descrizioni in questa tabella si riferiscono al caricamento di un componente aggiuntivo VSTO manualmente o a livello di codice. Per caricare un componente aggiuntivo VSTO manualmente, selezionare la casella di controllo accanto al componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** nell'applicazione. Per caricare un componente aggiuntivo VSTO a livello di codice, impostare la proprietà <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> dell'oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO su **true**.

|Valore decimale|Stato del componente aggiuntivo VSTO|Comportamento di caricamento del componente aggiuntivo VSTO|Descrizione|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Scaricato|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se il componente aggiuntivo VSTO viene caricato correttamente, il valore di **LoadBehavior** rimane impostato su 0, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è caricato.|
|1|Caricato|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Sebbene la finestra di dialogo **componenti aggiuntivi COM** indichi che il componente aggiuntivo VSTO viene caricato dopo l'avvio dell'applicazione, il componente aggiuntivo VSTO non viene caricato finché non viene caricato manualmente o a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 0 e rimane tale dopo la chiusura dell'applicazione.|
|2|Scaricato|Viene caricato all'avvio|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 3 e rimane tale dopo la chiusura dell'applicazione.|
|3\.|Caricato|Viene caricato all'avvio|L'applicazione tenta di caricare il componente aggiuntivo VSTO all'avvio. Questo è il valore predefinito quando si compila o si pubblica un componente aggiuntivo VSTO in Visual Studio.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 3. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 2 e rimane tale dopo la chiusura dell'applicazione.|
|8|Scaricato|Viene caricato su richiesta|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 9.|
|9|Caricato|Viene caricato su richiesta|Il componente aggiuntivo VSTO verrà caricato solo quando richiesto dall'applicazione, ad esempio quando un utente fa clic su un elemento dell'interfaccia utente che usa la funzionalità del componente aggiuntivo VSTO, come un pulsante personalizzato della barra multifunzione.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 9, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è attualmente caricato. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 8.|
|16|Caricato|Viene caricato la prima volta e successivamente su richiesta|Impostare questo valore se si vuole che il componente aggiuntivo VSTO venga caricato su richiesta. L'applicazione carica il componente aggiuntivo VSTO quando viene eseguita dall'utente per la prima volta. Alla successiva esecuzione dell'applicazione, verranno caricati tutti gli elementi dell'interfaccia utente definiti dal componente aggiuntivo VSTO, ma quest'ultimo non verrà caricato finché l'utente non fa clic su un elemento dell'interfaccia utente associato al componente aggiuntivo VSTO.<br /><br /> Quando l'applicazione carica correttamente il componente aggiuntivo VSTO per la prima volta, il valore di **LoadBehavior** rimane impostato su 16 mentre il componente aggiuntivo VSTO è caricato. Dopo la chiusura dell'applicazione, il valore di **LoadBehavior** viene impostato su 9.|

## <a name="see-also"></a>Vedere anche
- [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
