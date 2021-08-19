---
title: Voci del Registro di sistema VSTO componenti aggiuntivi
description: Informazioni su come creare un set specifico di voci del Registro di sistema quando si distribuiscono VSTO componenti aggiuntivi creati usando Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6577f42f053649e47a92615ae40e76f45f3c0c6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099555"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Voci del Registro di sistema VSTO componenti aggiuntivi
  È necessario creare un set specifico di voci del Registro di sistema quando si distribuiscono componenti aggiuntivi VSTO creati con Visual Studio. Queste voci del Registro di sistema forniscono informazioni che consentono all'applicazione di Microsoft Office di individuare e caricare il componente aggiuntivo VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Quando si compila il progetto, Visual Studio crea queste voci del Registro di sistema nel computer di sviluppo, in modo che sia possibile eseguire il componente aggiuntivo VSTO ed effettuarne il debug con facilità. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del Registro di sistema vengono create automaticamente nel computer dell'utente finale. Se si usa Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del Registro di sistema nel computer dell'utente finale.

 Per altre informazioni sull'uso delle voci del Registro di sistema durante il processo di caricamento per i componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> In questo argomento la dicitura *ID componente aggiuntivo* rappresenta l'identificatore univoco del componente aggiuntivo VSTO. Per impostazione predefinita, l'ID è il nome dell'assembly del componente aggiuntivo VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrare VSTO componenti aggiuntivi per l'utente corrente e per tutti gli utenti
 Un componente aggiuntivo VSTO installato può essere registrato in due modi diversi:

- Solo per l'utente corrente, ovvero è disponibile solo per l'utente connesso al computer quando VSTO è installato il componente aggiuntivo. In questo caso, le voci del Registro di sistema vengono create nel **HKEY_CURRENT_USER**.

- Per tutti gli utenti, ovvero qualsiasi utente che accede al computer può usare il componente VSTO componente aggiuntivo. In questo caso, le voci del Registro di sistema vengono create **in HKEY_LOCAL_MACHINE**.

  Tutti i componenti aggiuntivi VSTO creati con Visual Studio possono essere registrati per l'utente corrente. Tuttavia, i componenti aggiuntivi VSTO possono essere registrati per tutti gli utenti solo in determinati scenari. Questi scenari dipendono dalla versione di Microsoft Office installata nel computer e dal modo in cui è stato distribuito il componente aggiuntivo VSTO.

### <a name="deployment-type"></a>Tipo di distribuzione
 Se si usa ClickOnce per distribuire un componente aggiuntivo VSTO, quest'ultimo può essere registrato solo per l'utente corrente. Questo perché ClickOnce supporta solo la creazione di chiavi in **HKEY_CURRENT_USER**. Se si vuole registrare un componente aggiuntivo VSTO per tutti gli utenti di un computer, è necessario distribuirlo tramite Windows Installer. Per altre informazioni su questi tipi di distribuzione, vedere Deploy [an Office solution by using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) and Deploy an Office solution by using Windows [Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Voci del Registro di sistema
 Le voci VSTO del Registro di sistema del componente aggiuntivo  necessarie si trovano nelle chiavi del Registro di sistema seguenti, dove Radice è **HKEY_CURRENT_USER** o **HKEY_LOCAL_MACHINE a** seconda che l'installazione sia per l'utente corrente o per tutti gli utenti.

|Office Applicazione|Percorso di configurazione|
|------------------|------------------|
|Visio|*ROOT*\Software\Microsoft \\ *Visio*\Addins \\ *add-in ID*|
|Tutti gli altri|*Root*\Software\Microsoft\Office \\ *Office application name*\Addins \\ *add-in ID*|

> [!NOTE]
> Se il programma di installazione è mirato a tutti gli utenti in un Windows a 64 bit, è consigliabile che includa due voci del Registro di sistema, una sotto il HKEY_LOCAL_MACHINE\Software\Microsoft e una nel nodo \\ **HKEY_LOCAL_MACHINE\SoftwareWOW6432Node**\Microsoft hive. Ciò è dovuto al fatto che gli utenti possono usare versioni a 32 bit o a 64 bit Office nel computer.
>
>Se il programma di installazione ha come destinazione l'utente corrente, non è necessario installarlo nel nodo WOW6432 perché il percorso HKEY_CURRENT_USER\Software condiviso.
>
>Per altre informazioni, vedere Dati delle applicazioni a [32 e 64 bit nel Registro di sistema](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 Nella tabella seguente sono elencate le voci presenti in questa chiave del Registro di sistema.

|Voce|Type|valore|
|-----------|----------|-----------|
|**Descrizione**|REG_SZ|Obbligatorio. Breve descrizione del componente aggiuntivo VSTO.<br /><br /> Questa descrizione viene visualizzata quando l'utente seleziona il componente aggiuntivo VSTO nel riquadro **Componenti aggiuntivi** della finestra di dialogo **Opzioni** nell'applicazione di Microsoft Office.|
|**FriendlyName**|REG_SZ|Obbligatorio. Nome descrittivo del componente aggiuntivo VSTO visualizzato nella finestra di dialogo **Componenti aggiuntivi COM** dell'applicazione di Microsoft Office. Il valore predefinito è l'ID del componente aggiuntivo VSTO.|
|**LoadBehavior**|REG_DWORD|Obbligatorio. Valore che specifica quando l'applicazione tenta di caricare il componente aggiuntivo VSTO e lo stato corrente del componente aggiuntivo VSTO (caricato o scaricato).<br /><br /> Per impostazione predefinita, questo valore è impostato su 3, a indicare che il componente aggiuntivo VSTO viene caricato all'avvio. Per altre informazioni, vedere [Valori di LoadBehavior.](#LoadBehavior) **Nota:**  Se un utente disabilita il VSTO componente aggiuntivo, tale azione modifica il valore **LoadBehavior** nell'hive HKEY_CURRENT_USER **registro.** Per ogni utente, il valore del **valore Di LoadBehavior** nell'hive HKEY_CURRENT_USER esegue l'override del **valore loadBehavior** predefinito definito nell'hive **HKEY_LOCAL_MACHINE.**|
|**Manifesto**|REG_SZ|Obbligatorio. Percorso completo del manifesto della distribuzione del componente aggiuntivo VSTO. Può essere un percorso contenuto nel computer locale, una condivisione di rete (UNC) o un server Web (HTTP).<br /><br /> Se si usa Windows Installer per distribuire la soluzione, è necessario aggiungere il prefisso **file:///** al percorso di **manifesto** . È anche necessario aggiungere la **stringa&#124;vstolocal** (ovvero il carattere barra **verticale&#124;** seguito da **vstolocal**) alla fine di questo percorso. Il suffisso garantisce che la soluzione venga caricata dalla cartella di installazione e non dalla cache ClickOnce. Per altre informazioni, vedere [Deploy an Office solution by using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Nota:**  Quando si compila un componente VSTO nel computer di sviluppo, Visual Studio aggiunge automaticamente la&#124;**vstolocal** a questa voce del Registro di sistema.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Voci del Registro di sistema per Outlook modulo
 Se si crea un'area del modulo personalizzata in un componente aggiuntivo VSTO per Outlook, vengono usate voci aggiuntive del Registro di sistema per registrare l'area con Outlook. Queste voci vengono create in una chiave del Registro di sistema diversa per ogni classe di messaggio supportata dall'area. Queste chiavi del Registro di sistema si trova nel percorso seguente, dove *Radice* **è** HKEY_CURRENT_USER o **HKEY_LOCAL_MACHINE**.

 *Classe* di messaggio Root \Software\Microsoft\Office\Outlook\FormRegions \\ 

 Analogamente alle altre voci del Registro di sistema condivise da tutti i componenti aggiuntivi VSTO, Visual Studio crea le voci relative all'area del modulo nel computer di sviluppo durante la compilazione del progetto. Se si usa ClickOnce per distribuire il componente aggiuntivo VSTO, le voci del Registro di sistema vengono create automaticamente nel computer dell'utente finale. Se si usa Windows Installer per distribuire il componente aggiuntivo VSTO, è necessario configurare il progetto InstallShield Limited Edition per creare le voci del Registro di sistema nel computer dell'utente finale.

 Per altre informazioni sulle voci del Registro di sistema dell'area del modulo, vedere Specificare il percorso di [un'area del modulo in un modulo personalizzato.](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form) Per altre informazioni sulle aree Outlook modulo, vedere [Creare Outlook modulo.](../vsto/creating-outlook-form-regions.md)

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a> Valori di LoadBehavior
 La voce **LoadBehavior** nella chiave *ROOT*\Software\Microsoft\Office \\ *application name*\Addins \\ *add-in ID* contiene una combinazione bit per bit di valori che specificano il comportamento in fase di esecuzione del componente aggiuntivo VSTO. Il bit di ordine più basso (valori 0 e 1) indica se il componente aggiuntivo VSTO è attualmente caricato o scaricato. Gli altri bit indicano quando l'applicazione tenta di caricare il componente aggiuntivo VSTO.

 In genere, la voce **LoadBehavior** deve essere impostata su 0, 3 o 16 (in decimale) quando il componente aggiuntivo VSTO viene installato nei computer degli utenti finali. Per impostazione predefinita, Visual Studio imposta la voce **LoadBehavior** del componente aggiuntivo VSTO su 3 quando questo viene compilato o pubblicato.

 Nella tabella seguente sono elencati tutti i valori possibili della voce **LoadBehavior** . Alcune descrizioni in questa tabella si riferiscono al caricamento di un componente aggiuntivo VSTO manualmente o a livello di codice. Per caricare un componente aggiuntivo VSTO manualmente, selezionare la casella di controllo accanto al componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** nell'applicazione. Per caricare un componente aggiuntivo VSTO a livello di codice, impostare la proprietà <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> dell'oggetto <xref:Microsoft.Office.Core.COMAddIn> che rappresenta il componente aggiuntivo VSTO su **true**.

|Valore decimale|Stato del componente aggiuntivo VSTO|Comportamento di caricamento del componente aggiuntivo VSTO|Descrizione|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Unloaded|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se il componente aggiuntivo VSTO viene caricato correttamente, il valore di **LoadBehavior** rimane impostato su 0, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è caricato.|
|1|Loaded|Non viene caricato automaticamente|L'applicazione non tenta mai di caricare il componente aggiuntivo VSTO automaticamente. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Anche se la finestra di dialogo Componenti aggiuntivi **COM** indica che il componente aggiuntivo VSTO viene caricato dopo l'avvio dell'applicazione, il componente aggiuntivo VSTO non viene caricato fino a quando non viene caricato manualmente o a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 0 e rimane tale dopo la chiusura dell'applicazione.|
|2|Unloaded|Viene caricato all'avvio|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 3 e rimane tale dopo la chiusura dell'applicazione.|
|3|Loaded|Viene caricato all'avvio|L'applicazione tenta di caricare il componente aggiuntivo VSTO all'avvio. Questo è il valore predefinito quando si compila o si pubblica un componente aggiuntivo VSTO in Visual Studio.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 3. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 2 e rimane tale dopo la chiusura dell'applicazione.|
|8|Unloaded|Viene caricato su richiesta|L'applicazione non tenta di caricare automaticamente il componente aggiuntivo VSTO. L'utente può provare a caricare manualmente il componente aggiuntivo VSTO oppure quest'ultimo può essere caricato a livello di codice.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 9.|
|9|Loaded|Viene caricato su richiesta|Il componente aggiuntivo VSTO verrà caricato solo quando richiesto dall'applicazione, ad esempio quando un utente fa clic su un elemento dell'interfaccia utente che usa la funzionalità del componente aggiuntivo VSTO, come un pulsante personalizzato della barra multifunzione.<br /><br /> Se l'applicazione carica correttamente il componente aggiuntivo VSTO, il valore di **LoadBehavior** rimane impostato su 9, ma lo stato del componente aggiuntivo VSTO nella finestra di dialogo **Componenti aggiuntivi COM** viene aggiornato per indicare che il componente aggiuntivo VSTO è attualmente caricato. Se si verifica un errore durante il caricamento del componente aggiuntivo VSTO, il valore di **LoadBehavior** diventa 8.|
|16|Loaded|Viene caricato la prima volta e successivamente su richiesta|Impostare questo valore se si vuole che il componente aggiuntivo VSTO venga caricato su richiesta. L'applicazione carica il componente aggiuntivo VSTO quando viene eseguita dall'utente per la prima volta. Alla successiva esecuzione dell'applicazione, verranno caricati tutti gli elementi dell'interfaccia utente definiti dal componente aggiuntivo VSTO, ma quest'ultimo non verrà caricato finché l'utente non fa clic su un elemento dell'interfaccia utente associato al componente aggiuntivo VSTO.<br /><br /> Quando l'applicazione carica correttamente il componente aggiuntivo VSTO per la prima volta, il valore di **LoadBehavior** rimane impostato su 16 mentre il componente aggiuntivo VSTO è caricato. Dopo la chiusura dell'applicazione, il valore di **LoadBehavior** viene impostato su 9.|

## <a name="see-also"></a>Vedi anche
- [Architettura delle Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Creare Office soluzioni](../vsto/building-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
 