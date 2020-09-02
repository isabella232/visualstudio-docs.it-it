---
title: Creazione di applicazioni ClickOnce per la distribuzione da altri utenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3307fc124f50e8c9f73749293c36f53be36c5e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "71252454"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Creare applicazioni ClickOnce per la distribuzione da parte di terzi
Non tutti gli sviluppatori che creano distribuzioni ClickOnce pianificano di distribuire le applicazioni stesse. Molti di essi comunicano l'applicazione usando ClickOnce e quindi rilasciano i file a un cliente, ad esempio un'azienda di grandi dimensioni. Il cliente diventa quello responsabile dell'hosting dell'applicazione nella rete. In questo argomento vengono illustrati alcuni dei problemi inerenti a tali distribuzioni nelle versioni del .NET Framework precedenti alla versione 3,5. Viene quindi descritta una nuova soluzione fornita utilizzando la nuova funzionalità "utilizza manifesto per l'attendibilità" nel .NET Framework 3,5. Infine, si conclude con le strategie consigliate per la creazione di distribuzioni ClickOnce per i clienti che usano ancora versioni precedenti del .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemi relativi alla creazione di distribuzioni per i clienti
 Si verificano diversi problemi quando si prevede di fornire una distribuzione a un cliente. Il primo problema riguarda la firma del codice. Per poter essere distribuiti in una rete, il manifesto di distribuzione e il manifesto dell'applicazione di una distribuzione ClickOnce devono entrambi essere firmati con un certificato digitale. In questo modo si chiede se utilizzare il certificato dello sviluppatore o il certificato del cliente per la firma dei manifesti.

 La questione del certificato da usare è fondamentale, in quanto l'identità di un'applicazione ClickOnce è basata sulla firma digitale del manifesto di distribuzione. Se lo sviluppatore firma il manifesto della distribuzione, può causare conflitti se il cliente è un'azienda di grandi dimensioni e più di una divisione della società distribuisce una versione personalizzata dell'applicazione.

 Si immagini, ad esempio, che Adventure Works abbia un reparto finanziario e un reparto risorse umane. Entrambi i reparti hanno una licenza per un'applicazione ClickOnce di Microsoft Corporation che genera report dai dati archiviati in un database SQL. Microsoft fornisce a ogni reparto una versione dell'applicazione personalizzata per i propri dati. Se le applicazioni sono firmate con lo stesso certificato Authenticode, un utente che tenta di utilizzare entrambe le applicazioni potrebbe riscontrare un errore, in quanto ClickOnce considera la seconda applicazione identica alla prima. In questo caso, il cliente può riscontrare effetti collaterali imprevisti e indesiderati che includono la perdita di tutti i dati archiviati localmente dall'applicazione.

 Un ulteriore problema correlato alla firma del codice è l' `deploymentProvider` elemento nel manifesto di distribuzione, che indica a ClickOnce dove cercare gli aggiornamenti dell'applicazione. Questo elemento deve essere aggiunto al manifesto di distribuzione prima della firma. Se questo elemento viene aggiunto in seguito, il manifesto di distribuzione deve essere firmato nuovamente.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Richiedi al cliente di firmare il manifesto della distribuzione
 Una soluzione a questo problema di distribuzioni non univoche consiste nel fare in modo che lo sviluppatore firmi il manifesto dell'applicazione e che il cliente firmi il manifesto della distribuzione. Sebbene questo approccio funzioni, introduce altri problemi. Poiché un certificato Authenticode deve rimanere un asset protetto, il cliente non può semplicemente assegnare il certificato allo sviluppatore per firmare la distribuzione. Sebbene il cliente possa firmare autonomamente il manifesto di distribuzione usando gli strumenti disponibili gratuitamente con il .NET Framework SDK, questo potrebbe richiedere una conoscenza tecnica più che il cliente sia disposto o in grado di fornire. In questi casi, lo sviluppatore in genere crea un'applicazione, un sito Web o un altro meccanismo mediante il quale il cliente può inviare la propria versione dell'applicazione per la firma.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>L'effetto della firma del cliente sulla sicurezza delle applicazioni ClickOnce
 Anche se lo sviluppatore e il cliente accettano che il cliente deve firmare il manifesto dell'applicazione, questo genera altri problemi che racchiudono l'identità dell'applicazione, soprattutto quando si applica alla distribuzione di applicazioni attendibili. Per ulteriori informazioni su questa funzionalità, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md). Supponiamo che Adventure Works desideri configurare i computer client in modo che tutte le applicazioni fornite da Microsoft Corporation vengano eseguite con attendibilità totale. Se Adventure Works firma il manifesto della distribuzione, ClickOnce utilizzerà la firma di sicurezza di Adventure Work per determinare il livello di attendibilità dell'applicazione.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Creare distribuzioni dei clienti usando il manifesto dell'applicazione per l'attendibilità
 ClickOnce nella .NET Framework 3,5 contiene una nuova funzionalità che offre agli sviluppatori e ai clienti una nuova soluzione per lo scenario di firma dei manifesti. Il manifesto dell'applicazione ClickOnce supporta un nuovo elemento denominato `<useManifestForTrust>` che consente agli sviluppatori di indicare che la firma digitale del manifesto dell'applicazione è quella da usare per prendere decisioni di attendibilità. Lo sviluppatore usa gli strumenti per la creazione di pacchetti ClickOnce, ad esempio *Mage.exe*, *MageUI.exe*e Visual Studio, per includere questo elemento nel manifesto dell'applicazione, nonché per incorporare il nome dell'editore e il nome dell'applicazione nel manifesto.

 Quando `<useManifestForTrust>` si usa, non è necessario che il manifesto di distribuzione sia firmato con un certificato Authenticode emesso da un'autorità di certificazione. Al contrario, può essere firmato con un certificato autofirmato. Un certificato autofirmato viene generato dal cliente o dallo sviluppatore utilizzando gli strumenti standard di .NET Framework SDK e quindi applicato al manifesto di distribuzione utilizzando gli strumenti di distribuzione ClickOnce standard. Per ulteriori informazioni, vedere [Makecert](/windows/desktop/SecCrypto/makecert).

 L'uso di un certificato autofirmato per il manifesto di distribuzione presenta diversi vantaggi. Eliminando la necessità per il cliente di ottenere o creare il proprio certificato Authenticode, `<useManifestForTrust>` semplifica la distribuzione per il cliente, consentendo allo sviluppatore di mantenere la propria identità di personalizzazione sull'applicazione. Il risultato è un set di distribuzioni firmate più sicure e con identità di applicazione univoche. In questo modo si elimina il potenziale conflitto che può verificarsi quando si distribuisce la stessa applicazione a più clienti.

 Per informazioni dettagliate su come creare una distribuzione ClickOnce con `<useManifestForTrust>` abilitata, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e che conserva le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione
 Per comprendere meglio il funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione, si consideri l'esempio seguente. Un'applicazione ClickOnce destinata a .NET Framework 3,5 viene creata da Microsoft. Il manifesto dell'applicazione usa l' `<useManifestForTrust>` elemento ed è firmato da Microsoft. Adventure Works firma il manifesto di distribuzione usando un certificato autofirmato. I client Adventure Works sono configurati in modo da considerare attendibile qualsiasi applicazione firmata da Microsoft.

 Quando un utente fa clic su un collegamento al manifesto di distribuzione, ClickOnce installa l'applicazione nel computer dell'utente. Le informazioni sul certificato e sulla distribuzione identificano l'applicazione in modo univoco in ClickOnce nel computer client. Se l'utente tenta di installare nuovamente la stessa applicazione da un percorso diverso, ClickOnce può usare questa identità per determinare che l'applicazione esiste già nel client.

 Successivamente, ClickOnce esamina il certificato Authenticode usato per firmare il manifesto dell'applicazione, che determina il livello di attendibilità concesso da ClickOnce. Poiché Adventure Works ha configurato i client in modo che considerino attendibile le applicazioni firmate da Microsoft, a questa applicazione ClickOnce viene concessa l'attendibilità totale. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Creare distribuzioni cliente per versioni precedenti
 Cosa accade se uno sviluppatore distribuisce applicazioni ClickOnce ai clienti che usano versioni precedenti del .NET Framework? Le sezioni seguenti riepilogano diverse soluzioni consigliate, insieme ai vantaggi e agli svantaggi di ognuno di essi.

### <a name="sign-deployments-on-behalf-of-customer"></a>Firma le distribuzioni per conto del cliente
 Una possibile strategia di distribuzione prevede che lo sviluppatore crei un meccanismo per firmare le distribuzioni per conto dei clienti, usando la chiave privata del cliente. In questo modo si impedisce allo sviluppatore di dover gestire chiavi private o più pacchetti di distribuzione. Lo sviluppatore fornisce solo la stessa distribuzione per ogni cliente. È il cliente a personalizzarlo per il proprio ambiente tramite il servizio di firma.

 Uno svantaggio di questo metodo è il tempo e la spesa necessari per implementarlo. Sebbene un servizio di questo tipo possa essere compilato usando gli strumenti disponibili in .NET Framework SDK, aggiungerà più tempo di sviluppo al ciclo di vita del prodotto.

 Come indicato in precedenza in questo argomento, un altro svantaggio è che la versione dell'applicazione di ogni cliente avrà la stessa identità dell'applicazione, che potrebbe causare conflitti. Se si tratta di un problema, lo sviluppatore può modificare il campo del nome usato durante la generazione del manifesto di distribuzione per assegnare a ogni applicazione un nome univoco. Verrà creata un'identità separata per ogni versione dell'applicazione ed eliminare eventuali conflitti di identità potenziali. Questo campo corrisponde all' `-Name` argomento per Mage.exe e al campo **nome** nella scheda **nome** della MageUI.exe.

 Ad esempio, si può dire che lo sviluppatore ha creato un'applicazione denominata application1. Anziché creare una singola distribuzione con il campo nome impostato su Application1, lo sviluppatore può creare diverse distribuzioni con una variante specifica del cliente per questo nome, ad esempio Application1-customerA, Application1-CustomerB e così via.

### <a name="deploy-using-a-setup-package"></a>Eseguire la distribuzione usando un pacchetto di installazione
 Una seconda possibile strategia di distribuzione consiste nel generare un progetto di installazione Microsoft per eseguire la distribuzione iniziale dell'applicazione ClickOnce. Questo può essere fornito in uno dei diversi formati: come distribuzione MSI, come un eseguibile di installazione (. EXE) o come file CAB (CAB) insieme a uno script batch.

 Utilizzando questa tecnica, lo sviluppatore fornisce al cliente una distribuzione che include i file dell'applicazione, il manifesto dell'applicazione e un manifesto di distribuzione che funge da modello. Il cliente eseguirebbe il programma di installazione, che richiederebbe un URL di distribuzione (il percorso del server o della condivisione file da cui gli utenti installeranno l'applicazione ClickOnce), nonché un certificato digitale. È inoltre possibile che l'applicazione di installazione scelga di richiedere opzioni di configurazione ClickOnce aggiuntive, ad esempio l'intervallo di controllo degli aggiornamenti. Una volta raccolte queste informazioni, il programma di installazione genera il manifesto della distribuzione reale, lo firma e pubblica l'applicazione ClickOnce nel percorso del server designato.

 In questa situazione, il cliente può firmare il manifesto di distribuzione in tre modi:

1. Il cliente può utilizzare un certificato valido emesso da un'autorità di certificazione (CA).

2. Come variante di questo approccio, il cliente può scegliere di firmare il manifesto di distribuzione con un certificato autofirmato. Lo svantaggio è che l'applicazione visualizzerà le parole "autore sconosciuto" quando all'utente viene chiesto se installarlo. Tuttavia, il vantaggio è che impedisce ai clienti più piccoli di dover dedicare tempo e denaro necessari per un certificato emesso da un'autorità di certificazione.

3. Infine, lo sviluppatore può includere il proprio certificato autofirmato nel pacchetto di installazione. In questo articolo vengono introdotti i potenziali problemi relativi all'identità dell'applicazione illustrata in precedenza in questo argomento.

   Lo svantaggio del metodo del progetto di distribuzione del programma di installazione è il tempo e la spesa necessari per creare un'applicazione di distribuzione personalizzata.

### <a name="have-customer-generate-deployment-manifest"></a>Genera manifesto di distribuzione del cliente
 Una terza strategia di distribuzione può essere quella di consegnare al cliente solo i file dell'applicazione e il manifesto dell'applicazione. In questo scenario il cliente è responsabile dell'uso di .NET Framework SDK per generare e firmare il manifesto della distribuzione.

 Lo svantaggio di questo metodo è che richiede al cliente di installare gli strumenti di .NET Framework SDK e di avere uno sviluppatore o un amministratore di sistema esperto nel loro utilizzo. Alcuni clienti possono richiedere una soluzione che non richiede alcuno sforzo tecnico.

## <a name="see-also"></a>Vedere anche
- [Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza firma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e mantiene le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)