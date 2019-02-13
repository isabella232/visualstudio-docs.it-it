---
title: Windows Communication Foundation e WCF Data Services
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 677d68aab6f6dfdb39f12ba33002758f61a03a31
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919941"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servizi Windows Communication Foundation e dati WCF in Visual Studio

Visual Studio offre strumenti per l'utilizzo di Windows Communication Foundation (WCF) e WCF Data Services, le tecnologie Microsoft per la creazione di applicazioni distribuite. In questo argomento viene fornita un'introduzione ai servizi da una prospettiva di Visual Studio. Per la documentazione completa, vedere [WCF Data Services 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Che cos'è WCF?

Windows Communication Foundation (WCF) è un framework unificato per la creazione di applicazioni distribuite sicure, affidabili, transazionali e interoperabile. Sostituisce meno recenti tecnologie di comunicazione interprocesso, ad esempio servizi web ASMX, .NET Remoting, Enterprise Services (DCOM) e MSMQ. WCF offre le funzionalità di tutte queste tecnologie in un modello di programmazione unificato. Ciò semplifica l'esperienza di sviluppo di applicazioni distribuite.

### <a name="what-are-wcf-data-services"></a>Quali sono i servizi dati WCF

WCF Data Services è un'implementazione del protocollo OData (Open Data) standard.  WCF Data Services consente di esporre dati tabulari come un set di API REST, che consente di restituire dati utilizzando verbi HTTP standard quali GET, POST, PUT o DELETE. Sul lato server, WCF Data Services progressivamente sostituiti dagli [API Web ASP.NET](http://www.asp.net/web-api) per la creazione di nuovi servizi OData. La libreria client di WCF Data Services continua a essere una buona scelta per l'utilizzo di servizi OData in un'applicazione .NET da Visual Studio (**Project** > **Aggiungi riferimento al servizio**). Per altre informazioni, vedere [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Modello di programmazione WCF

Il modello di programmazione WCF si basa sulla comunicazione tra due entità: un servizio WCF e un client WCF. Il modello di programmazione è incapsulato nel <xref:System.ServiceModel> dello spazio dei nomi in .NET Framework.

### <a name="wcf-service"></a>Servizio WCF

Un servizio WCF si basa su un'interfaccia che definisce un contratto tra il servizio e il client. È contrassegnato con un <xref:System.ServiceModel.ServiceContractAttribute> attributo, come illustrato nel codice seguente:

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Si definisce funzioni o metodi esposti da un servizio WCF, contrassegnandoli con un <xref:System.ServiceModel.OperationContractAttribute> attributo.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

Inoltre, è possibile esporre i dati serializzati, si contrassegna un tipo composto con un <xref:System.Runtime.Serialization.DataContractAttribute> attributo. Ciò consente il data binding in un client.

Dopo aver definiti un'interfaccia e i relativi metodi, vengono incapsulati in una classe che implementa l'interfaccia. Una singola classe di servizio WCF può implementare più contratti di servizio.

Un servizio WCF viene esposta per l'utilizzo tramite è noto come un *endpoint*. L'endpoint fornisce l'unico modo per comunicare con il servizio. è possibile accedere al servizio tramite un riferimento diretto come si farebbe con le altre classi.

Un endpoint è costituito da un indirizzo, un'associazione e un contratto. Definisce l'indirizzo in cui il servizio si trova; potrebbe trattarsi di un URL, un indirizzo FTP, o una rete o un percorso locale. Un'associazione definisce il modo in cui comunica con il servizio. Le associazioni di WCF forniscono un modello versatile per specificare un protocollo come HTTP o FTP, un meccanismo di sicurezza, ad esempio l'autenticazione di Windows o nomi utente e password e altro ancora. Un contratto include le operazioni esposte dalla classe del servizio WCF.

È possibile esporre più endpoint per un unico servizio WCF. In questo modo diverso ai client di comunicare con lo stesso servizio in modi diversi. Ad esempio, un servizio di servizi bancari potrebbe fornire un endpoint per i dipendenti e l'altro per i clienti esterni, ognuna delle quali Usa un indirizzo diverso, l'associazione e/o del contratto.

### <a name="wcf-client"></a>client WCF

Un client WCF è costituito da un *proxy* che consente a un'applicazione comunicare con un servizio WCF e un endpoint che corrisponde a un endpoint definito per il servizio. La generazione del proxy sul lato client nel *app. config* file e include informazioni sui tipi e metodi esposti dal servizio. Per i servizi che espongono più endpoint, il client può selezionare quello più adatto alle proprie necessità, ad esempio, per comunicare tramite HTTP e utilizzare l'autenticazione di Windows.

Dopo aver creato un client WCF, si fa riferimento il servizio nel codice esattamente come si farebbe qualsiasi altro oggetto. Ad esempio, per chiamare il `GetData` metodo illustrato in precedenza, è necessario scrivere codice simile al seguente:

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Strumenti WCF in Visual Studio

Visual Studio offre strumenti che consentono di creare servizi WCF e i client WCF. Per una procedura dettagliata che illustra gli strumenti, vedere [procedura dettagliata: Creazione di un servizio WCF semplice in Windows Forms

### <a name="create-and-test-wcf-services"></a>Creare e testare i servizi WCF

È possibile utilizzare i modelli di Visual Studio WCF come base per creare rapidamente il proprio servizio. È quindi possibile utilizzare Host automatico servizio di WCF e Client di prova WCF per eseguire il debug e testare il servizio. Questi strumenti insieme forniscono un rapido e comodo debug e ciclo di test ed eliminano la necessità di eseguire il commit a un modello di hosting in una fase iniziale.

#### <a name="wcf-templates"></a>Modelli di WCF

Modelli di Visual Studio WCF offrono una struttura di classe di base per lo sviluppo del servizio. Sono disponibili in diversi modelli WCF il **Aggiungi nuovo progetto** nella finestra di dialogo. Sono inclusi progetti lLibrary del servizio WCF, siti Web di servizio WCF e i modelli di elemento di servizio WCF.

Quando si seleziona un modello, i file vengono aggiunti per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio. Tutti gli attributi necessari sono già aggiunto, la creazione di un tipo di "Hello World" semplice del servizio, e non è necessario scrivere alcun codice. È, naturalmente, dovranno aggiungere il codice per fornire funzioni e metodi per il servizio del mondo reale, ma i modelli forniscono la base.

Per altre informazioni sui modelli di WCF, vedere [modelli di Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Host servizio WCF

Quando si avvia il debugger di Visual Studio (premendo **F5**) per un progetto di servizio WCF, lo strumento Host del servizio WCF viene avviato automaticamente per ospitare il servizio in locale. Host servizio WCF enumera i servizi in un progetto di servizio WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio che trova.

Mediante Host servizio WCF, è possibile testare un servizio WCF senza scrivere codice aggiuntivo o eseguire il commit a un host specifico durante lo sviluppo.

Per altre informazioni sull'Host del servizio WCF, vedere [host del servizio WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Client di prova WCF

Lo strumento Client di prova WCF consente di immettere parametri di test, inviare tale input a un servizio WCF e visualizzare la risposta restituita dal servizio. Fornisce un servizio utile testare esperienza quando si combina con Host servizio WCF. Trovare lo strumento nel *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* cartella.

Quando si preme **F5** per eseguire il debug di un progetto di servizio WCF, i Client di prova WCF si apre e visualizza un elenco di endpoint di servizio definiti nel file di configurazione. È possibile testare i parametri e avviare il servizio e ripetere questa procedura per testare e convalidare il servizio in modo continuo.

Per altre informazioni sui Client di prova WCF, vedere [WCF test client (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>L'accesso ai servizi WCF in Visual Studio

Visual Studio semplifica l'attività di creazione client WCF, la generazione automatica di un proxy e un endpoint per i servizi aggiunti usando il **Aggiungi riferimento al servizio** nella finestra di dialogo. Tutte le informazioni necessarie per la configurazione viene aggiunta per il *app. config* file. La maggior parte dei casi, tutto ciò che è necessario eseguire è creare un'istanza del servizio per poterlo usare.

Il **Aggiungi riferimento al servizio** nella finestra di dialogo consente di immettere l'indirizzo per un servizio o per cercare un servizio che viene definito nella soluzione. La finestra di dialogo restituisce un elenco dei servizi e le operazioni fornite da tali servizi. Consente inoltre di definire lo spazio dei nomi mediante il quale si farà riferimento ai servizi nel codice.

Il **riferimenti al servizio configurare** nella finestra di dialogo consente di personalizzare la configurazione per un servizio. È possibile modificare l'indirizzo per un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto di messaggio e configurare riutilizzo dei tipi.

## <a name="how-to-select-a-service-endpoint"></a>Procedura: Selezionare un endpoint di servizio

Alcuni servizi Windows Communication Foundation (WCF) espongono più endpoint tramite il quale un client può comunicare con il servizio. Ad esempio, un servizio può esporre un endpoint che utilizza un binding HTTP e il nome utente e la protezione delle password e un secondo endpoint che utilizza FTP e l'autenticazione di Windows. Il primo endpoint potrebbe essere utilizzato da applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere usato in una rete intranet.

In tal caso, è possibile specificare il `endpointConfigurationName` come parametro al costruttore per un riferimento al servizio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Per selezionare un endpoint di servizio

1.  Aggiungere un riferimento a un servizio WCF facendo clic sul nodo del progetto in **Esplora soluzioni** e scegliendo **Aggiungi riferimento al servizio**.

2.  Nell'Editor di codice, aggiungere un costruttore per il riferimento al servizio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Sostituire *ServiceReference* con lo spazio dei nomi per il riferimento al servizio e sostituisci *Service1Client* con il nome del servizio.

3.  Consente di visualizzare un elenco di IntelliSense che include gli overload del costruttore. Selezionare il `endpointConfigurationName As String` rapporto di overload.

4.  Dopo l'overload, digitare `=` *ConfigurationName*, dove *ConfigurationName* è il nome dell'endpoint a cui si desidera utilizzare.

    > [!NOTE]
    > Se non si conoscono i nomi degli endpoint disponibili, è possibile trovarli nel *app. config* file.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Per trovare gli endpoint disponibili per un servizio WCF

1.  Nella **Esplora soluzioni**, fare doppio clic il **app. config** file per il progetto che contiene il riferimento al servizio e quindi fare clic su **Open**. Il file viene visualizzato nell'Editor del codice.

2.  Cercare il `<Client>` tag nel file.

3.  Cercare di sotto di `<Client>` tag per un tag che inizia con `<Endpoint>`.

     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più `<Endpoint` tag.

4.  All'interno di `<EndPoint>` applicare un tag, si noterà una `name="` *nomeservizio* `"` parametro (in cui *nomeservizio* rappresenta il nome di un endpoint). Si tratta del nome per l'endpoint che può essere passato al `endpointConfigurationName As String` overload di un costruttore per un riferimento al servizio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Procedura: Chiamare un metodo del servizio in modo asincrono

La maggior parte dei metodi nei servizi Windows Communication Foundation (WCF) possono essere chiamati in modo sincrono o asincrono. Chiamata a un metodo in modo asincrono consente all'applicazione di continuare a lavorare durante il metodo viene chiamato quando opera su una connessione lenta.

Per impostazione predefinita, quando viene aggiunto un riferimento al servizio a un progetto, è configurato per chiamare i metodi in modo sincrono. È possibile modificare il comportamento di chiamata ai metodi in modo asincrono modificando un'impostazione nel **Configura riferimento al servizio** nella finestra di dialogo.

> [!NOTE]
> Questa opzione è impostata su una base per ogni servizio. Se un metodo per un servizio viene chiamato in modo asincrono, tutti i metodi devono essere chiamati in modo asincrono.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Per chiamare un metodo del servizio in modo asincrono

1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.

2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.

3.  Nel **Configura riferimento al servizio** finestra di dialogo, seleziona la **Genera operazioni asincrone** casella di controllo.

## <a name="how-to-bind-data-returned-by-a-service"></a>Procedura: Associare i dati restituiti da un servizio

È possibile associare dati restituiti da un servizio Windows Communication Foundation (WCF) a un controllo così come qualsiasi altra origine dati è possibile associare a un controllo. Quando si aggiunge un riferimento a un servizio WCF, se il servizio contiene tipi composti che restituiscono dati, vengono aggiunti automaticamente per il **Zdroje dat** finestra.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Per associare un controllo per singolo campo di dati restituito da un servizio WCF

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

   Viene visualizzata la finestra **Origini dati**.

2.  Nel **Zdroje dat** finestra, espandere il nodo per il riferimento al servizio. Tutti i tipi compositi restituiti per la visualizzazione del servizio.

3.  Espandere un nodo per un tipo. Vengono visualizzati i campi di dati per quel tipo.

4.  Selezionare un campo e fare clic sulla freccia giù per visualizzare un elenco di controlli che sono disponibili per il tipo di dati.

5.  Fare clic sul tipo di controllo a cui si desidera associare.

6.  Trascinare il campo in un form. Il controllo viene aggiunto al form, insieme a un <xref:System.Windows.Forms.BindingSource> componenti e una <xref:System.Windows.Forms.BindingNavigator> componente.

7.  Ripetere i passaggi da 4 a 6 per eventuali altri campi che si desidera associare.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Associare un controllo composito tipo restituito da un servizio WCF

1.  Nel **Data** dal menu **Mostra origini dati**. Viene visualizzata la finestra **Origini dati**.

2.  Nel **Zdroje dat** finestra, espandere il nodo per il riferimento al servizio. Tutti i tipi compositi restituiti per la visualizzazione del servizio.

3.  Selezionare un nodo per un tipo e fare clic sulla freccia giù per visualizzare un elenco delle opzioni disponibili.

4.  Fare clic su **DataGridView** per visualizzare i dati in una griglia oppure **dettagli** per visualizzare i dati in singoli controlli.

5.  Trascinare il nodo nel form. I controlli vengono aggiunti al modulo, insieme a un <xref:System.Windows.Forms.BindingSource> componenti e una <xref:System.Windows.Forms.BindingNavigator> componente.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedura: Configurare un servizio per riusare i tipi esistenti

Quando viene aggiunto un riferimento al servizio a un progetto, tutti i tipi definiti nel servizio vengono generati nel progetto locale. In molti casi, ciò consente di creare tipi duplicati quando un servizio Usa i tipi di .NET Framework comuni o i tipi sono definiti in una libreria condivisa.

Per evitare questo problema, i tipi negli assembly di riferimento sono condivisi per impostazione predefinita. Se si desidera disabilitare la condivisione di tipi per uno o più assembly, è possibile eseguire questa operazione nel **riferimenti al servizio configurare** nella finestra di dialogo.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Per disabilitare la condivisione di tipi in un unico assembly

1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.

2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.

3.  Nel **riferimenti al servizio configurare** finestra di dialogo **Riutilizza tipi negli assembly di riferimento specificati**.

4.  Selezionare la casella di controllo per ogni assembly in cui si desidera abilitare la condivisione dei tipi. Per disabilitare la condivisione di tipi per un assembly, lasciare deselezionata la casella di controllo.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Per disabilitare la condivisione di tipi in tutti gli assembly

1.  Nelle **Esplora soluzioni**, selezionare il riferimento al servizio.

2.  Nel **Project** menu, fare clic su **Configura riferimento al servizio**.

3.  Nel **riferimenti al servizio di configurare** della finestra di dialogo deseleziona le **Riutilizza tipi negli assembly di riferimento** casella di controllo.

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [Procedura dettagliata: Creazione di un servizio WCF semplice in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Fornisce informazioni dettagliate sulla creazione e utilizzo dei servizi WCF in Visual Studio. |
| [Procedura dettagliata: Creazione di un servizio dati WCF con WPF ed Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Fornisce informazioni dettagliate sulla procedura creare e usare WCF Data Services in Visual Studio. |
| [Uso degli strumenti di sviluppo WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Viene illustrato come creare e testare i servizi WCF in Visual Studio. |
| | [Procedura: Aggiungere, aggiornare o rimuovere un riferimento a WCF Data Services](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md) | Presenta alcuni errori comuni che possono verificarsi con i riferimenti al servizio e come evitarli. |
| [Debug dei servizi WCF](../debugger/debugging-wcf-services.md) | Vengono descritti problemi di debug comuni e le tecniche che possono verificarsi durante il debug di servizi WCF. |
| [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti. |
| [Finestra di dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md) | Descrive gli elementi dell'interfaccia utente di **Configura riferimento al servizio** nella finestra di dialogo. |

## <a name="reference"></a>Riferimenti

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)