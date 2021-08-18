---
title: Windows Communication Foundation e WCF Data Services
description: Esplorare Windows e i servizi WCF (Communication Foundation) WCF Data Services in Visual Studio, in modo da poter creare applicazioni distribuite.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 754f2b08f73b111ed8f62dedde17e2c133565d0a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059164"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Servizi Windows Communication Foundation e dati WCF in Visual Studio

Visual Studio strumenti per l'uso di Windows Communication Foundation (WCF) e WCF Data Services, tecnologie Microsoft per la creazione di applicazioni distribuite. In questo argomento viene fornita un'introduzione ai servizi Visual Studio punto di vista. Per la documentazione completa, vedere [WCF Data Services 4.5.](/dotnet/framework/data/wcf/index)

## <a name="what-is-wcf"></a>Che cos'è WCF?

Windows Communication Foundation (WCF) è un framework unificato per la creazione di applicazioni distribuite sicure, affidabili, transazionate e interoperativi. Sostituisce le tecnologie di comunicazione interprocesso meno recenti, ad esempio i servizi Web ASMX, .NET Remoting, Enterprise Services (DCOM) e MSMQ. WCF riunisce le funzionalità di tutte queste tecnologie in un modello di programmazione unificato. Ciò semplifica l'esperienza di sviluppo di applicazioni distribuite.

### <a name="what-are-wcf-data-services"></a>Quali sono i WCF Data Services

WCF Data Services è un'implementazione dello standard OData (Open Data).  WCF Data Services consente di esporre i dati tabulari come set di API REST, consentendo di restituire dati usando verbi HTTP standard, ad esempio GET, POST, PUT o DELETE. Sul lato server, i WCF Data Services vengono sostituiti da API Web ASP.NET [per](https://dotnet.microsoft.com/apps/aspnet/apis) la creazione di nuovi servizi OData. La WCF Data Services client continua a essere una buona scelta per l'utilizzo di servizi OData in un'applicazione .NET da Visual Studio **(Project**  >  **Aggiungi riferimento al servizio**). Per altre informazioni, vedere [WCF Data Services 4.5](/dotnet/framework/data/wcf).

### <a name="wcf-programming-model"></a>Modello di programmazione WCF

Il modello di programmazione WCF si basa sulla comunicazione tra due entità: un servizio WCF e un client WCF. Il modello di programmazione è incapsulato nello spazio <xref:System.ServiceModel> dei nomi in .NET.

### <a name="wcf-service"></a>Servizio WCF

Un servizio WCF è basato su un'interfaccia che definisce un contratto tra il servizio e il client. È contrassegnata con un <xref:System.ServiceModel.ServiceContractAttribute> attributo , come illustrato nel codice seguente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet6":::

Le funzioni o i metodi esposti da un servizio WCF vengono definiti contrassegnandoli con un <xref:System.ServiceModel.OperationContractAttribute> attributo .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

Inoltre, è possibile esporre i dati serializzati contrassegnando un tipo composito con un <xref:System.Runtime.Serialization.DataContractAttribute> attributo . In questo modo data binding in un client.

Dopo aver definito un'interfaccia e i relativi metodi, questi vengono incapsulati in una classe che implementa l'interfaccia . Una singola classe di servizio WCF può implementare più contratti di servizio.

Un servizio WCF viene esposto per l'utilizzo tramite ciò che è noto come *endpoint*. L'endpoint rappresenta l'unico modo per comunicare con il servizio. non è possibile accedere al servizio tramite un riferimento diretto come si farebbe con altre classi.

Un endpoint è costituito da un indirizzo, un'associazione e un contratto. L'indirizzo definisce dove si trova il servizio; può trattarsi di un URL, di un indirizzo FTP o di una rete o di un percorso locale. Un'associazione definisce la modalità di comunicazione con il servizio. Le associazioni WCF forniscono un modello versatile per specificare un protocollo, ad esempio HTTP o FTP, un meccanismo di sicurezza come l'autenticazione Windows o nomi utente e password e molto altro ancora. Un contratto include le operazioni esposte dalla classe del servizio WCF.

È possibile esporre più endpoint per un singolo servizio WCF. In questo modo client diversi possono comunicare con lo stesso servizio in modi diversi. Ad esempio, un servizio bancario potrebbe fornire un endpoint per i dipendenti e un altro per i clienti esterni, ognuno dei quali usa un indirizzo, un'associazione e/o un contratto diversi.

### <a name="wcf-client"></a>client WCF

Un client WCF è costituito da un *proxy* che consente a un'applicazione di comunicare con un servizio WCF e da un endpoint che corrisponde a un endpoint definito per il servizio. Il proxy viene generato sul lato client nel file *app.config* e include informazioni sui tipi e i metodi esposti dal servizio. Per i servizi che espongono più endpoint, il client può selezionare quello più adatto alle proprie esigenze, ad esempio per comunicare tramite HTTP e usare Windows autenticazione.

Dopo aver creato un client WCF, si fa riferimento al servizio nel codice come qualsiasi altro oggetto. Ad esempio, per chiamare il `GetData` metodo illustrato in precedenza, scrivere codice simile al seguente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

## <a name="wcf-tools-in-visual-studio"></a>Strumenti WCF in Visual Studio

Visual Studio strumenti che consentono di creare sia servizi WCF che client WCF. Per una procedura dettagliata che illustra gli strumenti, vedere Procedura dettagliata: Creazione di un servizio [WCF semplice in Windows Form.](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)

### <a name="create-and-test-wcf-services"></a>Creare e testare servizi WCF

È possibile usare i modelli Visual Studio WCF come base per creare rapidamente un servizio personalizzato. È quindi possibile usare l'host automatico del servizio WCF e il client di test WCF per eseguire il debug e il test del servizio. Questi strumenti insieme offrono un ciclo di debug e test rapido e pratico ed eliminano la necessità di eseguire il commit in un modello di hosting in una fase iniziale.

#### <a name="wcf-templates"></a>Modelli WCF

I modelli Visual Studio WCF forniscono una struttura di classi di base per lo sviluppo di servizi. Nella finestra di dialogo Aggiungi nuovo Project WCF sono disponibili **diversi** modelli WCF. Sono inclusi i progetti lLibrary del servizio WCF, i siti Web del servizio WCF e i modelli di elemento del servizio WCF.

Quando si seleziona un modello, vengono aggiunti file per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio. Tutti gli attributi necessari sono già stati aggiunti, creando un semplice tipo di servizio "Hello World" e non è stato necessario scrivere codice. Naturalmente, si vuole aggiungere codice per fornire funzioni e metodi per il servizio reale, ma i modelli forniscono le basi di base.

Per altre informazioni sui modelli WCF, vedere [Modelli Visual Studio WCF.](/dotnet/framework/wcf/wcf-vs-templates)

#### <a name="wcf-service-host"></a>Host servizio WCF

Quando si avvia il debugger Visual Studio (premendo **F5**) per un progetto di servizio WCF, lo strumento Host servizio WCF viene avviato automaticamente per ospitare il servizio in locale. L'host del servizio WCF enumera i servizi in un progetto di servizio WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio trovato.

Usando l'host del servizio WCF, è possibile testare un servizio WCF senza scrivere codice aggiuntivo o eseguire il commit in un host specifico durante lo sviluppo.

Per altre informazioni sull'host del servizio WCF, vedere Host del servizio [WCF (WcfSvcHost.exe).](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)

#### <a name="wcf-test-client"></a>Client di prova WCF

Lo strumento client di test WCF consente di immettere parametri di test, inviare l'input a un servizio WCF e visualizzare la risposta inviata dal servizio. Offre una pratica esperienza di test del servizio quando viene combinato con l'host del servizio WCF. Trovare lo strumento nella cartella *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE.*

Quando si preme **F5 per** eseguire il debug di un progetto di servizio WCF, viene aperto wcf test client e viene visualizzato un elenco di endpoint di servizio definiti nel file di configurazione. È possibile testare i parametri e avviare il servizio e ripetere questo processo per testare e convalidare continuamente il servizio.

Per altre informazioni sul client di test WCF, vedere [Client di test WCF (WcfTestClient.exe).](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)

### <a name="accessing-wcf-services-in-visual-studio"></a>Accesso ai servizi WCF in Visual Studio

Visual Studio semplifica l'attività di creazione di client WCF, generando automaticamente un proxy e un endpoint per i servizi aggiunti tramite la finestra di **Aggiungi riferimento al servizio** di dialogo. Tutte le informazioni di configurazione necessarie vengono aggiunte al file *app.config* file. Nella maggior parte dei casi, è necessario creare un'istanza del servizio per usarlo.

La **Aggiungi riferimento al servizio** finestra di dialogo consente di immettere l'indirizzo di un servizio o di cercare un servizio definito nella soluzione. La finestra di dialogo restituisce un elenco di servizi e le operazioni fornite da tali servizi. Consente inoltre di definire lo spazio dei nomi con cui si farà riferimento ai servizi nel codice.

La **finestra di dialogo Configura** riferimenti al servizio consente di personalizzare la configurazione per un servizio. È possibile modificare l'indirizzo per un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto di messaggio e configurare il riutilizzo dei tipi.

## <a name="how-to-select-a-service-endpoint"></a>Procedura: Selezionare un endpoint di servizio

Alcuni Windows Communication Foundation (WCF) espongono più endpoint tramite i quali un client può comunicare con il servizio. Ad esempio, un servizio potrebbe esporre un endpoint che usa un'associazione HTTP e la sicurezza di nome utente e password e un secondo endpoint che usa FTP e Windows autenticazione. Il primo endpoint può essere usato dalle applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere usato in una intranet.

In tal caso, è possibile specificare come `endpointConfigurationName` parametro al costruttore per un riferimento al servizio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Per selezionare un endpoint di servizio

1. Aggiungere un riferimento a un servizio WCF facendo clic con il pulsante destro del mouse sul nodo del **progetto** Esplora soluzioni e scegliendo **Aggiungi riferimento al servizio.**

2. Nell'editor del codice aggiungere un costruttore per il riferimento al servizio:

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Sostituire *ServiceReference con* lo spazio dei nomi per il riferimento al servizio e *Service1Client* con il nome del servizio.

3. Viene visualizzato un elenco di IntelliSense che include gli overload per il costruttore. Selezionare `endpointConfigurationName As String` l'overload.

4. Dopo l'overload digitare `=` *ConfigurationName*, dove *ConfigurationName* è il nome dell'endpoint che si vuole usare.

    > [!NOTE]
    > Se non si conoscono i nomi degli endpoint disponibili, è possibile trovarli nel file *app.config.*

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Per trovare gli endpoint disponibili per un servizio WCF

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse sul** fileapp.configper il progetto che contiene il riferimento al servizio e quindi scegliere **Apri.** Il file viene visualizzato nell'editor di codice.

2. Cercare il `<Client>` tag nel file .

3. Cercare sotto il `<Client>` tag un tag che inizia con `<Endpoint>` .

     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più `<Endpoint` tag.

4. `<EndPoint>`All'interno del tag è possibile trovare un parametro `name="` *SomeService* `"` (dove *SomeService* rappresenta il nome di un endpoint). Nome dell'endpoint che può essere passato `endpointConfigurationName As String` all'overload di un costruttore per un riferimento al servizio.

## <a name="how-to-call-a-service-method-asynchronously"></a>Procedura: Chiamare un metodo di servizio in modo asincrono

La maggior parte dei metodi nei Windows Communication Foundation (WCF) può essere chiamata in modo sincrono o asincrono. La chiamata asincrona di un metodo consente all'applicazione di continuare a funzionare mentre il metodo viene chiamato quando opera su una connessione lenta.

Per impostazione predefinita, quando un riferimento al servizio viene aggiunto a un progetto, viene configurato per chiamare i metodi in modo sincrono. È possibile modificare il comportamento per chiamare i metodi in modo asincrono modificando un'impostazione nella **finestra di dialogo** Configura riferimento al servizio .

> [!NOTE]
> Questa opzione è impostata in base al servizio. Se un metodo per un servizio viene chiamato in modo asincrono, tutti i metodi devono essere chiamati in modo asincrono.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Per chiamare un metodo di servizio in modo asincrono

1. In **Esplora soluzioni** selezionare il riferimento al servizio.

2. Nel menu **Project** fare clic su **Configura riferimento al servizio**.

3. Nella finestra **di dialogo Configura riferimento al** servizio selezionare la casella di controllo Genera operazioni **asincrone** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Procedura: Associare i dati restituiti da un servizio

È possibile associare i dati restituiti da un servizio Windows Communication Foundation (WCF) a un controllo esattamente come è possibile associare qualsiasi altra origine dati a un controllo . Quando si aggiunge un riferimento a un servizio WCF, se il servizio contiene tipi compositi che restituiscono dati, questi vengono aggiunti automaticamente alla **finestra Origini** dati.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Per associare un controllo a un singolo campo dati restituito da un servizio WCF

1. Scegliere **Mostra origini dati** dal menu **Dati**.

   Viene visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** espandere il nodo per il riferimento al servizio. Tutti i tipi compositi restituiti dalla visualizzazione del servizio.

3. Espandere un nodo per un tipo. Vengono visualizzati i campi dati per tale tipo.

4. Selezionare un campo e fare clic sulla freccia a discesa per visualizzare un elenco di controlli disponibili per il tipo di dati.

5. Fare clic sul tipo di controllo a cui si desidera eseguire l'associazione.

6. Trascinare il campo in un form. Il controllo viene aggiunto al form, insieme a un <xref:System.Windows.Forms.BindingSource> componente e a un componente <xref:System.Windows.Forms.BindingNavigator> .

7. Ripetere i passaggi da 4 a 6 per tutti gli altri campi da associare.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Per associare un controllo al tipo composito restituito da un servizio WCF

1. Scegliere **Mostra** origini **dati dal** menu Dati . Viene visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** espandere il nodo per il riferimento al servizio. Tutti i tipi compositi restituiti dalla visualizzazione del servizio.

3. Selezionare un nodo per un tipo e fare clic sulla freccia a discesa per visualizzare un elenco di opzioni disponibili.

4. Fare clic **su DataGridView** per visualizzare i dati in una griglia o **su Dettagli** per visualizzare i dati nei singoli controlli.

5. Trascinare il nodo nel form. I controlli vengono aggiunti al form, insieme a un <xref:System.Windows.Forms.BindingSource> componente e a un componente <xref:System.Windows.Forms.BindingNavigator> .

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Procedura: Configurare un servizio per riutilizzare i tipi esistenti

Quando un riferimento al servizio viene aggiunto a un progetto, tutti i tipi definiti nel servizio vengono generati nel progetto locale. In molti casi, ciò crea tipi duplicati quando un servizio usa tipi .NET comuni o quando i tipi sono definiti in una libreria condivisa.

Per evitare questo problema, i tipi negli assembly a cui si fa riferimento vengono condivisi per impostazione predefinita. Se si desidera disabilitare la condivisione dei tipi per uno o più assembly, è possibile farlo nella finestra **di** dialogo Configura riferimenti al servizio .

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Per disabilitare la condivisione dei tipi in un singolo assembly

1. In **Esplora soluzioni** selezionare il riferimento al servizio.

2. Nel menu **Project** fare clic su **Configura riferimento al servizio**.

3. Nella finestra **di dialogo Configura riferimenti al** servizio selezionare **Riutilizza tipi negli assembly a cui si fa riferimento specificati.**

4. Selezionare la casella di controllo per ogni assembly in cui si vuole abilitare la condivisione dei tipi. Per disabilitare la condivisione dei tipi per un assembly, lasciare deselezionata la casella di controllo.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Per disabilitare la condivisione dei tipi in tutti gli assembly

1. In **Esplora soluzioni** selezionare il riferimento al servizio.

2. Nel menu **Project** fare clic su **Configura riferimento al servizio**.

3. Nella finestra **di dialogo Configura riferimenti al** servizio deselezionare la casella di controllo **Riutilizza tipi** negli assembly a cui si fa riferimento.

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [Procedura dettagliata: creazione di un Windows Form semplice](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Fornisce una dimostrazione dettagliata della creazione e dell'uso dei servizi WCF in Visual Studio. |
| [Procedura dettagliata: Creazione di un servizio dati WCF con WPF ed Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Viene fornita una dimostrazione dettagliata di come creare e usare WCF Data Services in Visual Studio. |
| [Uso degli strumenti di sviluppo WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Viene illustrato come creare e testare i servizi WCF in Visual Studio. |
| | [Procedura: Aggiungere, aggiornare o rimuovere un riferimento al servizio dati WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Risoluzione dei problemi relativi ai riferimenti al servizio](../data-tools/troubleshooting-service-references.md) | Presenta alcuni errori comuni che possono verificarsi con i riferimenti al servizio e come impedirli. |
| [Debug di servizi WCF](../debugger/debugging-wcf-services.md) | Vengono descritti i problemi di debug comuni e le tecniche che possono verificarsi durante il debug dei servizi WCF. |
| [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti. |
| [Finestra di dialogo Configura riferimento al servizio](../data-tools/configure-service-reference-dialog-box.md) | Descrive gli elementi dell'interfaccia utente della **finestra di dialogo Configura riferimento al** servizio . |

## <a name="reference"></a>Riferimento

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
