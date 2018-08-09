---
title: Cenni preliminari sul modello a oggetti di Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b11757990a17a867776376454142e5b84ee82510
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008268"
---
# <a name="outlook-object-model-overview"></a>Cenni preliminari sul modello a oggetti di Outlook
  Per sviluppare componenti aggiuntivi VSTO per Microsoft Office Outlook, è possibile interagire con gli oggetti forniti dal modello a oggetti di Outlook. Il modello a oggetti di Outlook fornisce classi e interfacce che rappresentano elementi nell'interfaccia utente. Ad esempio, l'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'intera applicazione, l'oggetto <xref:Microsoft.Office.Interop.Outlook.Folder> rappresenta una cartelle che contiene messaggi di posta elettronica o altri elementi e l'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica.  
  
 Questo argomento fornisce una breve panoramica di alcuni degli oggetti principali del modello a oggetti di Outlook. Per le risorse in cui altre informazioni sull'intero modello a oggetti di Outlook, vedere [usare la documentazione del modello a oggetti Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [How do i: usare Outlook per creare una relazione attività personalizzata?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Accedere agli oggetti in un progetto di Outlook  
 Outlook offre numerosi oggetti con cui è possibile interagire. Per usare in modo efficace il modello a oggetti, è necessaria una familiarità con gli oggetti principali seguenti:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Folder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Oggetto Application  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> rappresenta l'applicazione Outlook ed è l'oggetto di livello massimo nel modello a oggetti di Outlook. Alcuni dei membri più importanti di questo oggetto includono i seguenti:  
  
-   Il [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metodo che è possibile usare per creare un nuovo elemento, ad esempio un messaggio di posta elettronica, attività o appuntamenti.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , che permette di accedere alle finestre che mostrano i contenuti di una cartella nell'interfaccia utente di Outlook.  
  
-   La proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , che permette di accedere alle finestre che mostrano i contenuti di un singolo elemento, ad esempio un messaggio di posta elettronica o una convocazione riunione.  
  
 Per ottenere un'istanza del <xref:Microsoft.Office.Interop.Outlook.Application> oggetto, usare il campo di applicazione dei `ThisAddIn` classe nel progetto. Per altre informazioni, vedere [programma VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Per evitare gli avvisi di sicurezza quando si usano proprietà e metodi bloccati dalla protezione del modello a oggetti di Outlook, ottenere gli oggetti di Outlook dal campo dell'applicazione dei `ThisAddIn` classe. Per altre informazioni, vedere [considerazioni specifiche sulla sicurezza per le soluzioni Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Oggetto Explorer  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> rappresenta una finestra che mostra i contenuti di una cartella che include elementi quali messaggi di posta elettronica, attività o appuntamenti. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> , eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Explorer> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> che ha attualmente lo stato attivo.  
  
-   Usare il metodo `GetExplorer` dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Folder> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Explorer> per la cartella corrente.  
  
### <a name="inspector-object"></a>Oggetto Inspector  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> rappresenta una finestra che mostra un singolo elemento, ad esempio un messaggio di posta elettronica, un'attività o un appuntamento. L'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> include metodi e proprietà che possono essere usati per modificare la finestra ed eventi che vengono generati quando la finestra viene modificata.  
  
 Per ottenere un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> , eseguire una delle operazioni seguenti:  
  
-   Usare la proprietà <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per accedere a tutti gli oggetti <xref:Microsoft.Office.Interop.Outlook.Inspector> in Outlook.  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> dell'oggetto <xref:Microsoft.Office.Interop.Outlook.Application> per ottenere l'oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che ha attualmente lo stato attivo.  
  
-   Usare il metodo `GetInspector` di un elemento specifico, ad esempio <xref:Microsoft.Office.Interop.Outlook.MailItem> o <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, per ottenere l'oggetto Inspector associato.  
  
### <a name="folder-object"></a>Oggetto della cartella  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.Folder> rappresenta una cartella che contiene messaggi di posta elettronica, contatti, attività e altri elementi. Outlook offre 16 oggetti <xref:Microsoft.Office.Interop.Outlook.Folder> predefiniti.  
  
 Gli oggetti <xref:Microsoft.Office.Interop.Outlook.Folder> predefiniti vengono definiti dai valori di enumerazione <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>. Ad esempio,  
  
 OlDefaultFolders. olFolderInbox corrispondente per il **posta in arrivo** cartella in Outlook.  
  
 Per un esempio che illustra come accedere a un valore predefinito <xref:Microsoft.Office.Interop.Outlook.Folder> e creare un nuovo <xref:Microsoft.Office.Interop.Outlook.Folder>, vedere [procedura: creare cartelle personalizzate](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Oggetto MailItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.MailItem> rappresenta un messaggio di posta elettronica. Gli oggetti<xref:Microsoft.Office.Interop.Outlook.MailItem> si trovano in genere nelle cartelle, ad esempio **Posta in arrivo**, **Posta inviata**e **Posta in uscita**. <xref:Microsoft.Office.Interop.Outlook.MailItem> espone proprietà e metodi che possono essere usati per creare e inviare messaggi di posta elettronica.  
  
 Per un esempio che illustra come creare un messaggio di posta elettronica, vedere [procedura: creare a livello di programmazione un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Oggetto AppointmentItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> rappresenta una riunione, un appuntamento singolo o un appuntamento o riunione ricorrente nella cartella **Calendario** . L'oggetto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> include metodi che eseguono azioni, quali la risposta o l'inoltro di una convocazione riunione, e proprietà che specificano i dettagli della riunione, ad esempio luogo e ora.  
  
 Per un esempio che illustra come creare un appuntamento, vedere [procedura: creare una convocazione riunione](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Oggetto TaskItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.TaskItem> rappresenta un'attività da eseguire entro un intervallo di tempo specificato. Gli oggetti<xref:Microsoft.Office.Interop.Outlook.TaskItem> si trovano nella cartella **Attività** .  
  
 Per creare un'attività, usare il [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) metodo per il <xref:Microsoft.Office.Interop.Outlook.Application> dell'oggetto e passare il valore <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> per il parametro.  
  
### <a name="contactitem-object"></a>Oggetto ContactItem  
 L'oggetto <xref:Microsoft.Office.Interop.Outlook.ContactItem>rappresenta un contatto nella cartella **Contatti** . Gli oggetti<xref:Microsoft.Office.Interop.Outlook.ContactItem> contengono diverse informazioni di contatto per le persone rappresentate, ad esempio via e numero civico, indirizzo di posta elettronica e numeri di telefono.  
  
 Per un esempio che illustra come creare un nuovo contatto, vedere [procedura: aggiungere a livello di codice una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Per un esempio che illustra come cercare un contatto esistente, vedere [procedura: eseguire la ricerca a livello di codice di un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Uso della documentazione sul modello a oggetti di Outlook  
 Per informazioni complete sul modello a oggetti di Outlook, è possibile usare il riferimento di assembly di interoperabilità primario di Outlook e il riferimento del modello a oggetti VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Riferimento all'assembly di interoperabilità primario  
 Il riferimento degli assembly di interoperabilità primari di Outlook documenta i tipi disponibili negli assembly di interoperabilità primari per Outlook 2010. Per altre informazioni, vedere [riferimento all'assembly di interoperabilità primario di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Oltre a fornire informazioni per tutti i tipi disponibili negli assembly di interoperabilità primari, questa documentazione fornisce anche informazioni aggiuntive sulla struttura degli assembly di interoperabilità primari ed esempi di codice per attività di automazione comuni di Outlook.  
  
### <a name="vba-object-model-reference"></a>Riferimento del modello a oggetti VBA  
 Nel riferimento del modello a oggetti VBA è illustrato il modello a oggetti di Outlook esposto al codice Visual Basic Applications (VBA). Per altre informazioni, vedere [riferimento del modello a oggetti di Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Tutti gli oggetti e i membri del riferimento del modello a oggetti VBA corrispondono ai tipi e ai membri dell'assembly di interoperabilità primario di Outlook. Ad esempio, l'oggetto Inspector nel riferimento del modello a oggetti VBA corrisponde alla <xref:Microsoft.Office.Interop.Outlook.Inspector> oggetto nell'assembly di interoperabilità primario di Outlook. Sebbene il riferimento del modello a oggetti di VBA fornisca esempi di codice per la maggior parte delle proprietà, dei metodi e degli eventi, è necessario convertire il codice VBA in questo riferimento a Visual Basic o a Visual C# se si vuole usarli in un progetto di componente aggiuntivo VSTO di Outlook creato con Visual Studio.  
  
### <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Lavorare con gli elementi di contatto](../vsto/working-with-contact-items.md)|Fornisce argomenti che illustrano come eseguire attività con i contatti.|  
|[Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di posta elettronica.|  
|[Con le cartelle di lavoro](../vsto/working-with-folders.md)|Fornisce argomenti che illustrano come eseguire attività con le cartelle.|  
|[Lavorare con gli elementi del calendario](../vsto/working-with-calendar-items.md)|Fornisce argomenti che illustrano come eseguire attività con gli elementi di calendario.|  
|[Procedura: determinare a livello di codice elemento Outlook corrente](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Illustra come visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato.|  
  