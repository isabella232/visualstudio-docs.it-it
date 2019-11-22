---
title: Servizi Windows Communication Foundation e WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c366ce44ab65ded62370dd3c219473089d5ca111
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299571"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servizi Windows Communication Foundation e dati WCF in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio sono disponibili strumenti per l'utilizzo di Windows Communication Foundation (WCF) e [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], le tecnologie Microsoft per la creazione di applicazioni distribuite. In questo argomento viene fornita un'introduzione ai servizi da una prospettiva [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per la documentazione completa, vedere [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a).

## <a name="what-is-wcf"></a>Che cos'è WCF?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] è un framework unificato per la creazione di applicazioni distribuite sicure, affidabili, transazionali e interoperabili. Sostituisce le tecnologie di comunicazione interprocesso precedenti, ad esempio i servizi Web ASMX, .NET Remoting, Enterprise Services (DCOM) e MSMQ. WCF combina le funzionalità di tutte le tecnologie in un modello di programmazione unificato. Questo semplifica l'esperienza di sviluppo di applicazioni distribuite.

#### <a name="what-are-wcf-data-services"></a>Che cosa sono WCF Data Services
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] è un'implementazione dello standard del protocollo OData (Open Data).  WCF Data Services consente di esporre i dati tabulari come un set di API REST, consentendo di restituire i dati usando verbi HTTP standard come GET, POST, PUT o DELETE. Sul lato server, WCF Data Services verranno sostituiti da [API Web ASP.NET](https://dotnet.microsoft.com/apps/aspnet/apis) per la creazione di nuovi servizi OData. La libreria client di WCF Data Services continua a essere una scelta ottimale per l'utilizzo di servizi OData in un'applicazione .NET da Visual Studio (**progetto &#124; Aggiungi riferimento al servizio**). Per altre informazioni, vedere [WCF Data Services 4.5](https://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Modello di programmazione WCF
 Il modello di programmazione WCF è basato sulla comunicazione tra due entità, ovvero un servizio WCF e un client WCF. Il modello di programmazione viene incapsulato nello spazio dei nomi <xref:System.ServiceModel> nel [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="wcf-service"></a>Servizio WCF
 Un servizio WCF si basa su un'interfaccia che definisce un contratto tra il servizio e il client. È contrassegnato con un attributo <xref:System.ServiceModel.ServiceContractAttribute>, come illustrato nel codice seguente:

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 Per definire funzioni o metodi esposti da un servizio WCF, è necessario contrassegnarli con un attributo <xref:System.ServiceModel.OperationContractAttribute>. Inoltre, è possibile esporre i dati serializzati contrassegnando un tipo composito con un attributo <xref:System.Runtime.Serialization.DataContractAttribute>. In questo modo è possibile data binding in un client.

 Dopo aver definito un'interfaccia e i relativi metodi, questi vengono incapsulati in una classe che implementa l'interfaccia. Una singola classe del servizio WCF può implementare più contratti di servizio.

 Un servizio WCF viene esposto per l'utilizzo tramite ciò che è noto come *endpoint*. L'endpoint fornisce l'unico modo per comunicare con il servizio. non è possibile accedere al servizio tramite un riferimento diretto come si farebbe con altre classi.

 Un endpoint è costituito da un indirizzo, un'associazione e un contratto. L'indirizzo definisce la posizione in cui si trova il servizio. potrebbe trattarsi di un URL, un indirizzo FTP o una rete o un percorso locale. Un'associazione definisce la modalità di comunicazione con il servizio. Le associazioni WCF forniscono un modello versatile per specificare un protocollo, ad esempio HTTP o FTP, un meccanismo di sicurezza, ad esempio l'autenticazione di Windows o nomi utente e password, e molto altro ancora. Un contratto include le operazioni esposte dalla classe del servizio WCF.

 È possibile esporre più endpoint per un singolo servizio WCF. Ciò consente a client diversi di comunicare con lo stesso servizio in modi diversi. Un servizio bancario, ad esempio, potrebbe fornire un endpoint per i dipendenti e un altro per i clienti esterni, ciascuno con un indirizzo, un'associazione e/o un contratto diverso.

#### <a name="wcf-client"></a>Client WCF
 Un client WCF è costituito da un *proxy* che consente a un'applicazione di comunicare con un servizio WCF e un endpoint che corrisponde a un endpoint definito per il servizio. Il proxy viene generato sul lato client nel file app. config e include informazioni sui tipi e i metodi esposti dal servizio. Per i servizi che espongono più endpoint, il client può selezionare quello più adatto alle proprie esigenze, ad esempio per comunicare tramite HTTP e utilizzare l'autenticazione di Windows.

 Dopo la creazione di un client WCF, si fa riferimento al servizio nel codice Analogamente a qualsiasi altro oggetto. Ad esempio, per chiamare il metodo `GetData` illustrato in precedenza, è necessario scrivere codice simile al seguente:

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Strumenti WCF in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre strumenti che consentono di creare sia i servizi WCF che i client WCF. Per una procedura dettagliata in cui vengono illustrati gli strumenti di, vedere [procedura dettagliata: creazione di un servizio WCF semplice in Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="creating-and-testing-wcf-services"></a>Creazione e test di servizi WCF
 È possibile utilizzare i modelli WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] come base per creare rapidamente un servizio personalizzato. È quindi possibile utilizzare l'host automatico del servizio WCF e il client di prova WCF per eseguire il debug e il test del servizio. Questi strumenti forniscono insieme un ciclo rapido e pratico di debug e test ed eliminano la necessità di eseguire il commit in un modello di hosting in una fase iniziale.

#### <a name="wcf-templates"></a>Modelli WCF
 I modelli di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF forniscono una struttura di classe di base per lo sviluppo del servizio. Nella finestra di dialogo **Aggiungi nuovo progetto** sono disponibili diversi modelli WCF. Sono inclusi i progetti della libreria di servizi WCF, i siti Web del servizio WCF e i modelli di elemento del servizio WCF.

 Quando si seleziona un modello, i file vengono aggiunti per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio. Tutti gli attributi necessari sono già stati aggiunti, creando un tipo di servizio "Hello World" semplice e non è necessario scrivere codice. Naturalmente, è necessario aggiungere il codice per fornire funzioni e metodi per il servizio reale, ma i modelli forniscono le fondamenta di base.

 Per ulteriori informazioni sui modelli WCF, vedere [modelli WCF di Visual Studio](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f).

#### <a name="wcf-service-host"></a>Host servizio WCF
 Quando si avvia il debugger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (premendo F5) per un progetto di servizio WCF, lo strumento host del servizio WCF viene avviato automaticamente per ospitare il servizio localmente. L'host del servizio WCF enumera i servizi in un progetto di servizio WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio rilevato.

 Utilizzando l'host del servizio WCF, è possibile testare un servizio WCF senza scrivere codice aggiuntivo o eseguire il commit in un host specifico durante lo sviluppo.

 Per ulteriori informazioni sull'host del servizio WCF, vedere [host del servizio WCF (WcfSvcHost. exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e).

#### <a name="wcf-test-client"></a>Client di prova WCF
 Lo strumento client di test WCF consente di immettere parametri di test, inviare l'input a un servizio WCF e visualizzare la risposta restituita dal servizio. Offre un'esperienza di test del servizio ottimale quando la si combina con l'host del servizio WCF. Lo strumento si trova nella cartella \Common7\IDE, che per Visual Studio 2015 installata nell'unità C: si trova qui: **c:\Programmi (x86) \Microsoft Visual Studio 14.0 \ Common7\IDE\\** .

 Quando si preme F5 per eseguire il debug di un progetto di servizio WCF, il client di prova WCF apre e visualizza un elenco di endpoint di servizio definiti nel file di configurazione. È possibile testare i parametri e avviare il servizio e ripetere il processo per verificare e convalidare costantemente il servizio.

 Per ulteriori informazioni sul client di prova WCF, vedere [client di prova WCF (WcfTestClient. exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7).

### <a name="accessing-wcf-services-in-visual-studio"></a>Accesso ai servizi WCF in Visual Studio
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] semplifica l'attività di creazione dei client WCF, la generazione automatica di un proxy e un endpoint per i servizi aggiunti tramite la finestra di dialogo **Aggiungi riferimento al servizio** . Tutte le informazioni di configurazione necessarie vengono aggiunte al file app. config. Nella maggior parte dei casi, è sufficiente creare un'istanza del servizio per usarlo.

 La finestra di dialogo **Aggiungi riferimento al servizio** consente di immettere l'indirizzo di un servizio o di cercare un servizio definito nella soluzione. La finestra di dialogo restituisce un elenco di servizi e le operazioni fornite da tali servizi. Consente inoltre di definire lo spazio dei nomi in base al quale si faranno riferimento ai servizi nel codice.

 La finestra di dialogo **Configura riferimenti al servizio** consente di personalizzare la configurazione per un servizio. È possibile modificare l'indirizzo di un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto di messaggio e configurare il riutilizzo dei tipi.

## <a name="how-to-select-a-service-endpoint"></a>Procedura: selezione di un endpoint di servizio
 Alcuni servizi di Windows Communication Foundation (WCF) espongono più endpoint tramite i quali un client può comunicare con il servizio. Ad esempio, un servizio può esporre un endpoint che usa un'associazione HTTP e una sicurezza con nome utente/password e un secondo endpoint che usa l'autenticazione FTP e Windows. Il primo endpoint può essere utilizzato da applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere utilizzato in una rete Intranet.

 In tal caso, è possibile specificare il `endpointConfigurationName` come parametro per il costruttore per un riferimento al servizio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>Per selezionare un endpoint di servizio

1. Per aggiungere un riferimento a un servizio WCF, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Aggiungi riferimento al servizio** .

2. Nell'editor di codice aggiungere un costruttore per il riferimento al servizio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Sostituire *ServiceReference* con lo spazio dei nomi per il riferimento al servizio e sostituire *ClientServizio1* con il nome del servizio.

3. Verrà visualizzato un elenco IntelliSense con gli overload del costruttore. Selezionare l'overload del `endpointConfigurationName As String`.

4. Dopo l'overload, digitare `=` *ConfigurationName*, dove *ConfigurationName* è il nome dell'endpoint che si desidera utilizzare.

    > [!NOTE]
    > Se non si conoscono i nomi degli endpoint disponibili, è possibile trovarli nel file app. config.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Per trovare gli endpoint disponibili per un servizio WCF

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul file app. config per il progetto che contiene il riferimento al servizio, quindi scegliere **Apri**. Il file verrà visualizzato nell'editor di codice.

2. Cercare il tag `<Client>` nel file.

3. Eseguire una ricerca sotto il tag `<Client>` per un tag che inizia con `<Endpoint>`.

     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più tag `<Endpoint`.

4. All'interno del tag `<EndPoint>` sarà presente un parametro di`"` `name="`*nomeservizio* (dove *nomeservizio* rappresenta il nome di un endpoint). Si tratta del nome dell'endpoint che può essere passato all'overload `endpointConfigurationName As String` di un costruttore per un riferimento al servizio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Procedura: chiamare un metodo di servizio in modo asincrono
 La maggior parte dei metodi nei servizi Windows Communication Foundation (WCF) può essere chiamata in modo sincrono o asincrono. La chiamata asincrona di un metodo consente all'applicazione di continuare a funzionare mentre il metodo viene chiamato quando opera su una connessione lenta.

 Per impostazione predefinita, quando un riferimento al servizio viene aggiunto a un progetto, è configurato per chiamare i metodi in modo sincrono. È possibile modificare il comportamento per chiamare i metodi in modo asincrono modificando un'impostazione nella finestra di dialogo **Configura riferimento al servizio** .

> [!NOTE]
> Questa opzione viene impostata in base al servizio. Se un metodo per un servizio viene chiamato in modo asincrono, tutti i metodi devono essere chiamati in modo asincrono.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>Per chiamare in modo asincrono un metodo del servizio

1. In **Esplora soluzioni**selezionare il riferimento al servizio.

2. Scegliere **Configura riferimento al servizio**dal menu **progetto** .

3. Nella finestra di dialogo **Configura riferimento al servizio** selezionare la casella di controllo **genera operazioni asincrone** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Procedura: associare dati restituiti da un servizio
 È possibile associare i dati restituiti da un servizio Windows Communication Foundation (WCF) a un controllo così come è possibile associare qualsiasi altra origine dati a un controllo. Quando si aggiunge un riferimento a un servizio WCF, se il servizio contiene tipi compositi che restituiscono dati, vengono aggiunti automaticamente alla finestra **origini dati** .

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Per associare un controllo a un singolo campo dati restituito da un servizio WCF

1. Scegliere **Mostra origini dati** dal menu **Dati**. Verrà visualizzata la finestra **origini dati** .

2. Nella finestra **origini dati** espandere il nodo per il riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.

3. Espandere un nodo per un tipo. Verranno visualizzati i campi dati per quel tipo.

4. Selezionare un campo e fare clic sulla freccia a discesa per visualizzare un elenco dei controlli disponibili per il tipo di dati.

5. Fare clic sul tipo di controllo a cui si desidera eseguire l'associazione.

6. Trascinare il campo su un form. Il controllo verrà aggiunto al form insieme a un componente <xref:System.Windows.Forms.BindingSource> e a un componente di <xref:System.Windows.Forms.BindingNavigator>.

7. Ripetere i passaggi da 4 a 6 per tutti gli altri campi che si desidera associare.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Per associare un controllo a un tipo composto restituito da un servizio WCF

1. Scegliere **Mostra origini dati**dal menu **dati** . Verrà visualizzata la finestra **origini dati** .

2. Nella finestra **origini dati** espandere il nodo per il riferimento al servizio. Verranno visualizzati tutti i tipi compositi restituiti dal servizio.

3. Selezionare un nodo per un tipo e fare clic sulla freccia a discesa per visualizzare un elenco delle opzioni disponibili.

4. Fare clic su **DataGridView** per visualizzare i dati in una griglia o **Dettagli** per visualizzare i dati nei singoli controlli.

5. Trascinare il nodo nel form. I controlli verranno aggiunti al form insieme a un componente <xref:System.Windows.Forms.BindingSource> e a un componente di <xref:System.Windows.Forms.BindingNavigator>.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedura: configurare un servizio per il riutilizzo di tipi esistenti
 Quando un riferimento al servizio viene aggiunto a un progetto, tutti i tipi definiti nel servizio vengono generati nel progetto locale. In molti casi, in questo caso vengono creati tipi duplicati quando un servizio usa tipi di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] comuni o quando i tipi sono definiti in una libreria condivisa.

 Per evitare questo problema, i tipi negli assembly a cui si fa riferimento vengono condivisi per impostazione predefinita. Se si desidera disabilitare la condivisione dei tipi per uno o più assembly, è possibile eseguire questa operazione nella finestra di dialogo **Configura riferimenti al servizio** .

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Per disabilitare la condivisione di tipi in un singolo assembly

1. In **Esplora soluzioni**selezionare il riferimento al servizio.

2. Scegliere **Configura riferimento al servizio**dal menu **progetto** .

3. Nella finestra di dialogo **Configura riferimenti al servizio** selezionare **Riutilizza tipi negli assembly a cui si fa riferimento specificati**.

4. Selezionare la casella di controllo per ogni assembly in cui si desidera abilitare la condivisione dei tipi. Per disabilitare la condivisione dei tipi per un assembly, lasciare deselezionata la casella di controllo.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>Per disabilitare la condivisione di tipi in tutti gli assembly

1. In **Esplora soluzioni**selezionare il riferimento al servizio.

2. Scegliere **Configura riferimento al servizio**dal menu **progetto** .

3. Nella finestra di dialogo **Configura riferimenti al servizio** deselezionare la casella **di controllo Riutilizza tipi in assembly a cui si fa riferimento** .

## <a name="related-topics"></a>Argomenti correlati

|Titolo|description|
|-----------|-----------------|
|[Procedura dettagliata: creazione di un Windows Form semplice](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Viene fornita una dimostrazione dettagliata della creazione e dell'utilizzo di servizi WCF in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Procedura dettagliata: creazione di un servizio dati WCF con WPF ed Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Viene fornita una dimostrazione dettagliata di come creare e utilizzare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Uso degli strumenti di sviluppo WCF](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|Viene illustrato come creare e testare i servizi WCF in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Procedura: aggiungere, aggiornare o rimuovere un riferimento al servizio](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|Viene descritto come aggiungere, aggiornare o rimuovere servizi WCF da un progetto di.|
|[Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Viene illustrato come fare riferimento e utilizzare [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|[Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md)|Presenta alcuni errori comuni che possono verificarsi con i riferimenti al servizio e come evitarli.|
|[Debug dei servizi WCF](../debugger/debugging-wcf-services.md)|Vengono descritti i problemi e le tecniche comuni di debug che possono verificarsi durante il debug dei servizi WCF.|
|[Panoramica del servizio di autenticazione Windows Communication Foundation](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|Viene descritto come utilizzare WCF per fornire un servizio ruolo per un sito Web.|
|[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti.|
|[Configura riferimento a servizio (finestra di dialogo)](../data-tools/configure-service-reference-dialog-box.md)|Vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Configura riferimento al servizio** .|

## <a name="reference"></a>Riferimenti
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>Vedere anche
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
