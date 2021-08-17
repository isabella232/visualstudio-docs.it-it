---
title: Considerazioni specifiche sulla sicurezza per Office soluzioni
description: Informazioni su come le funzionalità di sicurezza fornite da Microsoft .NET Framework e Microsoft Office possono aiutare a proteggere le soluzioni Office dalle minacce alla sicurezza.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 76d47af6c0a2c20fd80c9e83275f5a083e9ce899d98e079a28ac710355e0f6de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423852"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Considerazioni specifiche sulla sicurezza per Office soluzioni
  Le funzionalità di sicurezza fornite da Microsoft .NET Framework e Microsoft Office consentono di proteggere le soluzioni Office da potenziali rischi di sicurezza. Questo argomento illustra alcuni di tali rischi e fornisce suggerimenti utili su come proteggersi. Sono incluse anche informazioni su come le impostazioni di sicurezza di Microsoft Office possono influire sulle soluzioni Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Il codice attendibile viene riutilizzato in un nuovo documento dannoso
 Un utente malintenzionato potrebbe eseguire codice attendibile che dovrà essere usato per uno scopo specifico, ad esempio il download di informazioni personali per un'applicazione di occupazione, e riutilizzarlo in un altro documento, ad esempio un foglio di lavoro. Il codice non può stabilire che il documento originale non è in esecuzione e può introdurre altre minacce, ad esempio la divulgazione di informazioni personali o l'esecuzione di codice con privilegi di livello superiore, quando viene aperto da un altro utente. In alternativa, l'utente malintenzionato può modificare i dati nel foglio di lavoro in modo che, se inviati alla vittima, si comportino in modo imprevisto. Modificando i valori, le formule o le caratteristiche di presentazione di un foglio di lavoro collegato al codice, un utente malintenzionato può attaccare un altro utente inviando un file modificato. La modifica dei valori nel foglio di lavoro può anche consentire agli utenti di accedere a informazioni che non dovrebbero poter visualizzare.

 Dal momento che per l'esecuzione è necessario che il percorso dell'assembly e quello del documento abbiano evidenze sufficienti, questo tipo di attacco non è facilmente realizzabile. I documenti allegati a messaggi di posta elettronica o su server Intranet non attendibili, ad esempio, non hanno autorizzazioni sufficienti per essere eseguiti.

 Per consentire questo attacco, il codice deve essere scritto in modo da supportare decisioni basate su dati potenzialmente non attendibili. Si supponga di creare un foglio di lavoro che presenta una cella nascosta contenente il nome di un server di database. L'utente invia il foglio di lavoro a una pagina ASPX, che prova a connettersi a tale server usando l'autenticazione SQL e una password hardcoded dell'account sa. Un intruso potrebbe sostituire il contenuto della cella nascosta con un altro nome computer e ottenere la password dell'account sa. Per evitare questo problema non usare mai le password hardcoded e verificare sempre gli ID del server a fronte di un elenco interno di server noti come affidabili prima di accedere al server.

### <a name="recommendations"></a>Consigli

- Convalidare sempre l'input e i dati, che derivino dall'utente, dal documento, da un database, da un servizio Web, o da qualsiasi altra origine.

- Prestare attenzione nell'esposizione di determinati tipi di funzionalità, come l'acquisizione di dati privilegiati per conto dell'utente e il relativo inserimento in un foglio di lavoro non protetto.

- A seconda del tipo di applicazione, può rivelarsi utile verificare che il documento originale sia in esecuzione prima di eseguire qualsiasi codice. Ad esempio, verificare che venga eseguito da un documento archiviato in un percorso noto e sicuro.

- Se nell'applicazione vengono eseguite operazioni privilegiate, può essere opportuno visualizzare un avviso all'apertura del documento. È ad esempio possibile creare una schermata iniziale o una finestra di dialogo di avvio in cui viene segnalato che l'applicazione accederà a informazioni personali, consentendo all'utente di scegliere se continuare o annullare l'operazione. Se un avviso di questo tipo viene visualizzato da un documento apparentemente innocuo, l'utente finale potrà chiudere l'applicazione prima che si verifichino danni.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Il codice viene bloccato dalla protezione Outlook modello a oggetti
 Microsoft Office può limitare l'uso da parte del codice di determinate proprietà, metodi e oggetti nel modello a oggetti. Limitando l'accesso a questi oggetti, Outlook impedisce a worm e virus di posta elettronica di usare il modello a oggetti per scopi dannosi. Questa funzionalità di sicurezza è nota come protezione del modello a oggetti di Outlook. Se un componente aggiuntivo VSTO tenta di usare una proprietà o un metodo con restrizioni mentre la protezione del modello a oggetti è abilitata, Outlook visualizza un avviso di sicurezza che consente all'utente di arrestare l'operazione o consente all'utente di concedere l'accesso alla proprietà o al metodo per un periodo di tempo limitato. Se l'utente interrompe l'operazione, i componenti aggiuntivi di Outlook creati con le soluzioni Office in Visual Studio generano un'eccezione <xref:System.Runtime.InteropServices.COMException>.

 La protezione del modello a oggetti ha effetto sui componenti aggiuntivi in diversi modi, in base al fatto che Outlook venga usato o meno con Microsoft Exchange Server:

- Se Outlook non viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer.

- Se Outlook viene usato con Exchange, l'amministratore può abilitare o disabilitare la protezione del modello a oggetti per tutti i componenti aggiuntivi nel computer oppure specificare che determinati componenti aggiuntivi possano essere eseguiti senza la protezione del modello a oggetti. È anche possibile modificare il comportamento della protezione del modello a oggetti per alcune aree del modello a oggetti. Ad esempio, gli amministratori possono consentire automaticamente VSTO componenti aggiuntivi di inviare messaggi di posta elettronica a livello di codice, anche se la protezione del modello a oggetti è abilitata.

  A partire da Outlook 2007, il comportamento della protezione del modello a oggetti è stato modificato per migliorare l'esperienza utente e dello sviluppatore, aiutando al contempo a mantenere Outlook sicuro. Per altre informazioni, vedere [Modifiche alla sicurezza del codice in Outlook 2007.](/previous-versions/office/developer/office-2007/bb226709(v=office.12))

### <a name="minimize-object-model-guard-warnings"></a>Ridurre al minimo gli avvisi di protezione del modello a oggetti
 Per evitare la visualizzazione di avvisi di sicurezza quando si usano proprietà e metodi sottoposti a limitazioni, assicurarsi che il componente aggiuntivo VSTO ottenga oggetti di Outlook dal campo `Application` della classe `ThisAddIn` nel progetto. Per altre informazioni su questo campo, vedere [Componenti VSTO componenti aggiuntivi .](../vsto/programming-vsto-add-ins.md)

 Per la protezione del modello a oggetti possono essere considerati attendibili solo gli oggetti Outlook ottenuti da questo oggetto. Al contrario, oggetti ottenuti da un nuovo oggetto `Microsoft.Office.Interop.Outlook.Application` non vengono considerati attendibili e, se la protezione del modello a oggetti è attivata, le proprietà e i metodi sottoposti a limitazioni genereranno avvisi di sicurezza.

 Se la protezione del modello a oggetti è attivata, nell'esempio di codice seguente viene visualizzato un avviso di sicurezza. La proprietà `To` della classe `Microsoft.Office.Interop.Outlook.MailItem` è limitata dalla protezione del modello a oggetti. L'oggetto non è attendibile perché il codice lo ottiene da un oggetto creato usando `Microsoft.Office.Interop.Outlook.MailItem` `Microsoft.Office.Interop.Outlook.Application` l'operatore **new,** anziché ottenerlo dal `Application` campo .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet1":::

 Nell'esempio di codice seguente viene illustrato come usare la proprietà restricted To di un oggetto considerato `Microsoft.Office.Interop.Outlook.MailItem` attendibile dalla protezione del modello a oggetti. Il codice usa il campo `Application` attendibile per ottenere l'oggetto `Microsoft.Office.Interop.Outlook.MailItem`.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet2":::

> [!NOTE]
> Se Outlook viene usato con Exchange, il fatto che tutti gli oggetti Outlook siano ottenuti da `ThisAddIn.Application` non garantisce che il componente aggiuntivo VSTO riuscirà ad accedere al modello a oggetti di Outlook completo. Ad esempio, se un amministratore di Exchange imposta Outlook per negare automaticamente tutti i tentativi di accesso alle informazioni sull'indirizzo usando il modello a oggetti Outlook, Outlook non consentirà all'esempio di codice precedente di accedere alla proprietà To, anche se nell'esempio di codice viene utilizzato il campo `ThisAddIn.Application` attendibile.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Specificare i componenti aggiuntivi da considerare attendibili quando si usa Exchange
 Quando si usa Outlook con Exchange, gli amministratori possono specificare che per determinati componenti aggiuntivi è consentita l'esecuzione senza la protezione del modello a oggetti. I componenti aggiuntivi di Outlook creati usando le soluzioni Office in Visual Studio non possono essere considerati attendibili singolarmente, ma attendibili solo come gruppo.

 Outlook considera attendibile VSTO componente aggiuntivo basato su un codice hash della DLL del punto di ingresso VSTO componente aggiuntivo. Tutti Outlook VSTO componenti aggiuntivi che usano la stessa DLL del punto di ingresso [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] (*VSTOLoader.dll*). Ciò significa che se un amministratore considera attendibile qualsiasi componente aggiuntivo di VSTO destinato all'esecuzione di senza che sia presente la protezione del modello a oggetti, vengono considerati attendibili anche tutti gli altri componenti aggiuntivi VSTO che hanno come destinazione [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] l'oggetto . Per altre informazioni sull'attendibilità di componenti aggiuntivi specifici per l'esecuzione senza la protezione del modello a oggetti, vedere [Specificare il metodo usato da Outlook per gestire le caratteristiche di prevenzione dei virus](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Le modifiche alle autorizzazioni non vengono applicate immediatamente
 Se l'amministratore modifica le autorizzazioni per un documento o un assembly, per rendere effettive le modifiche gli utenti devono chiudere e quindi riavviare tutte le applicazioni di Office.

 L'applicazione delle nuove autorizzazioni può essere impedita anche da altre applicazioni che ospitano applicazioni Microsoft Office. Quando vengono modificati i criteri di sicurezza, è consigliabile che gli utenti chiudano tutte le applicazioni che usano Office in modo autonomo o tramite hosting.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Le impostazioni del Centro protezione Microsoft Office sistema non influiscono sui componenti aggiuntivi o sulle personalizzazioni a livello di documento
 Gli utenti possono impedire il caricamento dei componenti aggiuntivi VSTO impostando un'opzione nel **Centro protezione**. Tuttavia, i componenti aggiuntivi VSTO a livello di applicazione e le personalizzazioni a livello di documento creati con le soluzioni Office in Visual Studio non sono interessati da tali impostazioni di attendibilità.

 Se l'utente impedisce il caricamento dei componenti aggiuntivi usando il **Centro protezione**, non verranno caricati i tipi di componenti aggiuntivi seguenti:

- Componenti aggiuntivi VSTO COM gestiti e non gestiti

- Smart document gestiti e non gestiti

- Componenti aggiuntivi VSTO di automazione gestiti e non gestiti

- Componenti dati in tempo reale gestiti e non gestiti

  Le procedure seguenti descrivono come usare **Centro protezione** per limitare il caricamento dei componenti aggiuntivi in Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e Microsoft Office 2010. Queste procedure non influiscono sui componenti aggiuntivi o le personalizzazioni create usando gli strumenti di sviluppo di Office in Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>Per disabilitare i componenti aggiuntivi VSTO nelle applicazioni Microsoft Office 2010 e Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]

1. Scegliere la scheda **File** .

2. Scegliere il *pulsante ApplicationName* **Options (Opzioni nome** applicazione).

3. Nel riquadro delle categorie, scegliere **Centro protezione**.

4. Nel riquadro dei dettagli scegliere Impostazioni **Centro protezione**.

5. Nel riquadro delle categorie scegliere **Componenti aggiuntivi**.

6. Nel riquadro dei dettagli selezionare **Richiedi che i componenti aggiuntivi di applicazioni siano firmati da un autore attendibile** o **Disabilita tutti i componenti aggiuntivi delle applicazioni**.

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
