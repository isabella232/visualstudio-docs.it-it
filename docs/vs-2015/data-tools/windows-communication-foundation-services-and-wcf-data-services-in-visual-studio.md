---
title: Servizi Windows Communication Foundation e WCF Data Services in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 55b6ddc1d0e8e3a3caaee89547874e9e38115a17
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194688"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servizi Windows Communication Foundation e dati WCF in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio offre strumenti per l'utilizzo con Windows Communication Foundation (WCF) e [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], le tecnologie Microsoft per la creazione di applicazioni distribuite. In questo argomento viene fornita un'introduzione ai servizi da un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prospettiva. Per la documentazione completa, vedere [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).  
  
## <a name="what-is-wcf"></a>Che cos'è WCF?  
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] è un framework unificato per la creazione di applicazioni distribuite sicure, affidabili, transazionali e interoperabile. Sostituisce meno recenti tecnologie di comunicazione interprocesso, ad esempio servizi Web ASMX, .NET Remoting, Enterprise Services (DCOM) e MSMQ. WCF offre le funzionalità di tutte queste tecnologie in un modello di programmazione unificato. Ciò semplifica l'esperienza di sviluppo di applicazioni distribuite.  
  
#### <a name="what-are-wcf-data-services"></a>Quali sono i servizi dati WCF  
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] è un'implementazione del protocollo OData (Open Data) standard.  WCF Data Services consente di esporre dati tabulari come un set di API REST, che consente di restituire dati utilizzando verbi HTTP standard quali GET, POST, PUT o DELETE. Sul lato server, WCF Data Services progressivamente sostituiti dagli [API Web ASP.NET](http://www.asp.net/web-api) per la creazione di nuovi servizi OData. La libreria client di WCF Data Services continua a essere una buona scelta per l'utilizzo di servizi OData in un'applicazione .NET da Visual Studio (**progetto &#124; Aggiungi riferimento al servizio**). Per altre informazioni, vedere [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### <a name="wcf-programming-model"></a>Modello di programmazione WCF  
 Il modello di programmazione WCF si basa sulla comunicazione tra due entità: un servizio WCF e un client WCF. Il modello di programmazione è incapsulato nel <xref:System.ServiceModel> spazio dei nomi nel [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
#### <a name="wcf-service"></a>Servizio WCF  
 Un servizio WCF si basa su un'interfaccia che definisce un contratto tra il servizio e il client. È contrassegnato con un <xref:System.ServiceModel.ServiceContractAttribute> attributo, come illustrato nel codice seguente:  
  
 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]  
  
 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
 Si definisce funzioni o metodi esposti da un servizio WCF, contrassegnandoli con un <xref:System.ServiceModel.OperationContractAttribute> attributo. Inoltre, è possibile esporre i dati serializzati, si contrassegna un tipo composto con un <xref:System.Runtime.Serialization.DataContractAttribute> attributo. Ciò consente il data binding in un client.  
  
 Dopo aver definiti un'interfaccia e i relativi metodi, vengono incapsulati in una classe che implementa l'interfaccia. Una singola classe di servizio WCF può implementare più contratti di servizio.  
  
 Un servizio WCF viene esposta per l'utilizzo tramite è noto come un *endpoint*. L'endpoint fornisce l'unico modo per comunicare con il servizio. è possibile accedere al servizio tramite un riferimento diretto come si farebbe con le altre classi.  
  
 Un endpoint è costituito da un indirizzo, un'associazione e un contratto. Definisce l'indirizzo in cui il servizio si trova; potrebbe trattarsi di un URL, un indirizzo FTP, o una rete o un percorso locale. Un'associazione definisce il modo in cui comunica con il servizio. Le associazioni di WCF forniscono un modello versatile per specificare un protocollo come HTTP o FTP, un meccanismo di sicurezza, ad esempio l'autenticazione di Windows o nomi utente e password e altro ancora. Un contratto include le operazioni esposte dalla classe del servizio WCF.  
  
 È possibile esporre più endpoint per un unico servizio WCF. In questo modo diverso ai client di comunicare con lo stesso servizio in modi diversi. Ad esempio, un servizio di servizi bancari potrebbe fornire un endpoint per i dipendenti e l'altro per i clienti esterni, ognuna delle quali Usa un indirizzo diverso, l'associazione e/o del contratto.  
  
#### <a name="wcf-client"></a>Client WCF  
 Un client WCF è costituito da un *proxy* che consente a un'applicazione comunicare con un servizio WCF e un endpoint che corrisponde a un endpoint definito per il servizio. Il proxy viene generato sul lato client nel file app. config e include informazioni sui tipi e metodi esposti dal servizio. Per i servizi che espongono più endpoint, il client può selezionare quello più adatto alle proprie necessità, ad esempio, per comunicare tramite HTTP e utilizzare l'autenticazione di Windows.  
  
 Dopo aver creato un client WCF, si fa riferimento il servizio nel codice esattamente come si farebbe qualsiasi altro oggetto. Ad esempio, per chiamare il `GetData` metodo illustrato in precedenza, è necessario scrivere codice simile al seguente:  
  
 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
## <a name="wcf-tools-in-visual-studio"></a>Strumenti WCF in Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce strumenti che consentono di creare servizi WCF e i client WCF. Per una procedura dettagliata che illustra gli strumenti, vedere [procedura dettagliata: creazione di un semplice servizio WCF in Windows Form](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### <a name="creating-and-testing-wcf-services"></a>Creare e testare i servizi WCF  
 È possibile usare WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelli come base per creare rapidamente il proprio servizio. È quindi possibile utilizzare Host automatico servizio di WCF e Client di prova WCF per eseguire il debug e testare il servizio. Questi strumenti insieme forniscono un rapido e comodo debug e ciclo di test ed eliminano la necessità di eseguire il commit a un modello di hosting in una fase iniziale.  
  
#### <a name="wcf-templates"></a>Modelli di WCF  
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelli forniscono una struttura di classe di base per lo sviluppo del servizio. Sono disponibili in diversi modelli WCF il **Aggiungi nuovo progetto** nella finestra di dialogo. Sono inclusi i progetti libreria di servizi WCF, siti Web di servizi WCF e i modelli di elemento di servizio WCF.  
  
 Quando si seleziona un modello, i file vengono aggiunti per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio. Tutti gli attributi necessari sono già aggiunto, la creazione di un tipo di "Hello World" semplice del servizio, e non è necessario scrivere alcun codice. È, naturalmente, dovranno aggiungere il codice per fornire funzioni e metodi per il servizio del mondo reale, ma i modelli forniscono la base.  
  
 Per altre informazioni sui modelli di WCF, vedere [modelli di Visual Studio WCF](http://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).  
  
#### <a name="wcf-service-host"></a>Host servizio WCF  
 Quando si avvia il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] del debugger (premendo F5) per un progetto di servizio WCF, l'Host del servizio WCF dello strumento viene avviato automaticamente per ospitare il servizio in locale. Host servizio WCF enumera i servizi in un progetto di servizio WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio che trova.  
  
 Mediante Host servizio WCF, è possibile testare un servizio WCF senza scrivere codice aggiuntivo o eseguire il commit a un host specifico durante lo sviluppo.  
  
 Per altre informazioni sull'Host del servizio WCF, vedere [Host del servizio WCF (WcfSvcHost.exe)](http://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).  
  
#### <a name="wcf-test-client"></a>Client di prova WCF  
 Lo strumento Client di prova WCF consente di immettere parametri di test, inviare tale input a un servizio WCF e visualizzare la risposta restituita dal servizio. Fornisce un servizio utile testare esperienza quando si combina con Host servizio WCF. Lo strumento è reperibile nella cartella \Common7\IDE., ovvero per Visual Studio 2015 è installato nell'unità c: di seguito: **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**.  
  
 Quando si preme F5 per eseguire il debug di un progetto di servizio WCF, WCF Test Client apre e visualizza un elenco di endpoint di servizio definiti nel file di configurazione. È possibile testare i parametri e avviare il servizio e ripetere questa procedura per testare e convalidare il servizio in modo continuo.  
  
 Per altre informazioni sui Client di prova WCF, vedere [Client di prova WCF (WcfTestClient.exe)](http://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).  
  
### <a name="accessing-wcf-services-in-visual-studio"></a>L'accesso ai servizi WCF in Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] semplifica l'attività di creazione client WCF, la generazione automatica di un proxy e un endpoint per i servizi aggiunti usando il **Aggiungi riferimento al servizio** nella finestra di dialogo. Tutte le informazioni necessarie per la configurazione viene aggiunto al file app. config. La maggior parte dei casi, tutto ciò che è necessario eseguire è creare un'istanza del servizio per poterlo usare.  
  
 Il **Aggiungi riferimento al servizio** nella finestra di dialogo consente di immettere l'indirizzo per un servizio o per cercare un servizio che viene definito nella soluzione. La finestra di dialogo restituisce un elenco dei servizi e le operazioni fornite da tali servizi. Consente inoltre di definire lo spazio dei nomi mediante il quale si farà riferimento ai servizi nel codice.  
  
 Il **riferimenti al servizio configurare** nella finestra di dialogo consente di personalizzare la configurazione per un servizio. È possibile modificare l'indirizzo per un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto di messaggio e configurare riutilizzo dei tipi.  
  
## <a name="how-to-select-a-service-endpoint"></a>Procedura: selezionare un Endpoint di servizio  
 Alcuni servizi Windows Communication Foundation (WCF) espongono più endpoint tramite il quale un client può comunicare con il servizio. Ad esempio, un servizio può esporre un endpoint che utilizza un nome utente e dell'associazione HTTP / sicurezza delle password e un secondo endpoint che utilizza FTP e l'autenticazione di Windows. Il primo endpoint potrebbe essere utilizzato da applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere usato in una rete intranet.  
  
 In tal caso, è possibile specificare il `endpointConfigurationName` come parametro al costruttore per un riferimento al servizio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-select-a-service-endpoint"></a>Per selezionare un endpoint di servizio  
  
1.  Aggiungere un riferimento a un servizio WCF facendo clic sul nodo del progetto in Esplora soluzioni e scegliendo **Aggiungi riferimento al servizio**  
  
2.  Nell'Editor di codice, aggiungere un costruttore per il riferimento al servizio:  
  
    ```vb  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```csharp  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Sostituire *ServiceReference* con lo spazio dei nomi per il riferimento al servizio e sostituisci *Service1Client* con il nome del servizio.  
  
3.  Verrà visualizzato un elenco di IntelliSense con gli overload del costruttore. Selezionare il `endpointConfigurationName As String` rapporto di overload.  
  
4.  Dopo l'overload, digitare `=` *ConfigurationName*, dove *ConfigurationName* è il nome dell'endpoint a cui si desidera utilizzare.  
  
    > [!NOTE]
    >  Se non si conosce i nomi degli endpoint disponibili, è possibile trovarli nel file app. config.  
  
#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Per trovare gli endpoint disponibili per un servizio WCF  
  
1.  Nelle **Esplora soluzioni**, fare clic sul file app. config per il progetto che contiene il riferimento al servizio e quindi fare clic su **Open**. Il file verrà visualizzato nell'Editor del codice.  
  
2.  Cercare il `<Client>` tag nel file.  
  
3.  Cercare di sotto di `<Client>` tag per un tag che inizia con `<Endpoint>`.  
  
     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più `<Endpoint` tag.  
  
4.  All'interno di `<EndPoint>` tag sono disponibili un `name="` *nomeservizio* `"` parametro (dove *nomeservizio* rappresenta un nome di endpoint). Si tratta del nome per l'endpoint che può essere passato al `endpointConfigurationName As String` overload di un costruttore per un riferimento al servizio.  
  
## <a name="how-to-call-a-service-method-asynchronously"></a>Procedura: chiamare un metodo del servizio in modo asincrono  
 La maggior parte dei metodi nei servizi Windows Communication Foundation (WCF) possono essere chiamati in modo sincrono o asincrono. Chiamata a un metodo in modo asincrono consente all'applicazione di continuare a lavorare durante il metodo viene chiamato quando opera su una connessione lenta.  
  
 Per impostazione predefinita, quando viene aggiunto un riferimento al servizio a un progetto è configurato per chiamare i metodi in modo sincrono. È possibile modificare il comportamento di chiamata ai metodi in modo asincrono modificando un'impostazione nel **Configura riferimento al servizio** nella finestra di dialogo.  
  
> [!NOTE]
>  Questa opzione è impostata su una base per ogni servizio. Se un metodo per un servizio viene chiamato in modo asincrono, tutti i metodi devono essere chiamati in modo asincrono.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-call-a-service-method-asynchronously"></a>Per chiamare un metodo del servizio in modo asincrono  
  
1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.  
  
2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.  
  
3.  Nel **Configura riferimento al servizio** finestra di dialogo, seleziona la **Genera operazioni asincrone** casella di controllo.  
  
## <a name="how-to-bind-data-returned-by-a-service"></a>Procedura: associare dati restituiti da un servizio  
 È possibile associare dati restituiti da un servizio Windows Communication Foundation (WCF) a un controllo così come qualsiasi altra origine dati è possibile associare a un controllo. Quando si aggiunge un riferimento a un servizio WCF, se il servizio contiene tipi composti che restituiscono dati, vengono aggiunti automaticamente per il **Zdroje dat** finestra.  
  
#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Per associare un controllo per singolo campo di dati restituito da un servizio WCF  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**. Il **Zdroje dat** verrà visualizzata la finestra.  
  
2.  Nel **Zdroje dat** finestra, espandere il nodo per il riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Espandere un nodo per un tipo. Verranno visualizzati i campi di dati per quel tipo.  
  
4.  Selezionare un campo e fare clic sulla freccia giù per visualizzare un elenco di controlli che sono disponibili per il tipo di dati.  
  
5.  Fare clic sul tipo di controllo che si desidera associare.  
  
6.  Trascinare il campo in un form. Il controllo verrà aggiunto al form insieme a un <xref:System.Windows.Forms.BindingSource> componenti e una <xref:System.Windows.Forms.BindingNavigator> componente.  
  
7.  Ripetere i passaggi da 4 a 6 per eventuali altri campi che si desidera associare.  
  
#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Associare un controllo composito tipo restituito da un servizio WCF  
  
1.  Nel **Data** dal menu **Mostra origini dati**. Il **Zdroje dat** verrà visualizzata la finestra.  
  
2.  Nel **Zdroje dat** finestra, espandere il nodo per il riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Selezionare un nodo per un tipo e fare clic sulla freccia giù per visualizzare un elenco delle opzioni disponibili.  
  
4.  Fare clic su **DataGridView** per visualizzare i dati in una griglia oppure **dettagli** per visualizzare i dati in singoli controlli.  
  
5.  Trascinare il nodo nel form. Verranno aggiunti i controlli nel form insieme a un <xref:System.Windows.Forms.BindingSource> componenti e una <xref:System.Windows.Forms.BindingNavigator> componente.  
  
## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedura: configurare un servizio per riusare i tipi esistenti  
 Quando viene aggiunto un riferimento al servizio a un progetto, tutti i tipi definiti nel servizio vengono generati nel progetto locale. In molti casi, ciò consente di creare tipi duplicati quando si usa un servizio comune [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] tipi o quando i tipi sono definiti in una libreria condivisa.  
  
 Per evitare questo problema, i tipi negli assembly di riferimento sono condivisi per impostazione predefinita. Se si desidera disabilitare la condivisione di tipi per uno o più assembly, è possibile eseguire questa operazione nel **riferimenti al servizio configurare** nella finestra di dialogo.  
  
#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Per disabilitare la condivisione di tipi in un unico assembly  
  
1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.  
  
2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.  
  
3.  Nel **riferimenti al servizio configurare** finestra di dialogo **Riutilizza tipi negli assembly di riferimento specificati**.  
  
4.  Selezionare la casella di controllo per ogni assembly in cui si desidera abilitare la condivisione dei tipi. Per disabilitare la condivisione di tipi per un assembly, lasciare deselezionata la casella di controllo.  
  
#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Per disabilitare la condivisione di tipi in tutti gli assembly  
  
1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.  
  
2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.  
  
3.  Nel **riferimenti al servizio di configurare** della finestra di dialogo deseleziona le **Riutilizza tipi negli assembly di riferimento** casella di controllo.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura dettagliata: creazione di un Windows Form semplice](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Fornisce informazioni dettagliate sulla creazione e utilizzo di servizi WCF in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Procedura dettagliata: creazione di un servizio dati WCF con WPF ed Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Fornisce informazioni dettagliate sulla procedura creare e usare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Uso degli strumenti di sviluppo WCF](http://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Viene descritto come creare e testare i servizi WCF in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Viene descritto come aggiungere, aggiornare o rimuovere i servizi WCF da un progetto.|  
|[Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Viene illustrato come fare riferimento allo stesso modo [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md)|Presenta alcuni errori comuni che possono verificarsi con i riferimenti al servizio e come evitarli.|  
|[Debug dei servizi WCF](../debugger/debugging-wcf-services.md)|Vengono descritti problemi di debug comuni e le tecniche che possono verificarsi durante il debug di servizi WCF.|  
|[Panoramica sulle servizio di autenticazione di Windows Communication Foundation](http://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Viene descritto come usare WCF per fornire un servizio di ruolo per un sito Web.|  
|[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti.|  
|[Configura riferimento a servizio (finestra di dialogo)](../data-tools/configure-service-reference-dialog-box.md)|Descrive gli elementi dell'interfaccia utente di **Configura riferimento al servizio** nella finestra di dialogo.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)

