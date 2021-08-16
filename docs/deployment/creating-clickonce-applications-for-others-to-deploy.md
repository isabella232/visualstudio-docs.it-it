---
title: Creazione ClickOnce applicazioni per la distribuzione di | Microsoft Docs
description: Informazioni sulle applicazioni di ClickOnce ospitate dal cliente sviluppate in .NET Framework 3.5 e versioni precedenti del .NET Framework.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4d917ff087005264510b512f0a028c5621e74f8a6f79ab80ac9b119d647a1cc8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403997"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Creare applicazioni ClickOnce per la distribuzione da parte di terzi
Non tutti gli sviluppatori che creano ClickOnce le distribuzioni pianificano la distribuzione delle applicazioni stesse. Molti di essi si consegnino semplicemente l'applicazione usando ClickOnce e quindi consegnano i file a un cliente, ad esempio una grande azienda. Il cliente diventa il responsabile dell'hosting dell'applicazione nella propria rete. Questo argomento illustra alcuni dei problemi inerenti a tali distribuzioni nelle versioni del .NET Framework precedenti alla versione 3.5. Descrive quindi una nuova soluzione fornita usando la nuova funzionalità "Usa manifesto per l'attendibilità" nella versione .NET Framework 3.5. Infine, si conclude con le strategie consigliate per la creazione di ClickOnce per i clienti che usano ancora versioni precedenti del .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemi relativi alla creazione di distribuzioni per i clienti
 Quando si prevede di fornire una distribuzione a un cliente, si verificano diversi problemi. Il primo problema riguarda la firma del codice. Per poter essere distribuito in una rete, il manifesto della distribuzione e il manifesto dell'applicazione di un ClickOnce distribuzione devono essere firmati con un certificato digitale. Ciò pone la domanda se usare il certificato dello sviluppatore o il certificato del cliente durante la firma dei manifesti.

 La domanda sul certificato da usare è fondamentale, perché l'identità ClickOnce'applicazione è basata sulla firma digitale del manifesto della distribuzione. Se lo sviluppatore firma il manifesto della distribuzione, potrebbero verificarsi conflitti se il cliente è un'azienda di grandi dimensioni e più di una divisione dell'azienda distribuisce una versione personalizzata dell'applicazione.

 Si supponga, ad esempio, che Adventure Works abbia un reparto finanziario e un reparto risorse umane. Entrambi i reparti con licenza ClickOnce un'applicazione Microsoft Corporation che genera report dai dati archiviati in un database SQL. Microsoft fornisce a ogni reparto una versione dell'applicazione personalizzata per i propri dati. Se le applicazioni sono firmate con lo stesso certificato Authenticode, un utente che tenta di usare entrambe le applicazioni potrebbe riscontrare un errore, perché ClickOnce considererebbe la seconda applicazione identica alla prima. In questo caso, il cliente potrebbe sperimentare effetti collaterali imprevedibili e indesiderati che includono la perdita di tutti i dati archiviati localmente dall'applicazione.

 Un altro problema correlato alla firma del codice è l'elemento nel manifesto della distribuzione, che indica ClickOnce `deploymentProvider` dove cercare gli aggiornamenti dell'applicazione. Questo elemento deve essere aggiunto al manifesto della distribuzione prima di firmarlo. Se questo elemento viene aggiunto in seguito, il manifesto della distribuzione deve essere firmato nuovamente.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Richiedere al cliente di firmare il manifesto della distribuzione
 Una soluzione a questo problema di distribuzioni non univoche consiste nel fare in modo che lo sviluppatore firma il manifesto dell'applicazione e il cliente firma il manifesto della distribuzione. Anche se questo approccio funziona, introduce altri problemi. Poiché un certificato Authenticode deve rimanere un asset protetto, il cliente non può semplicemente fornire il certificato allo sviluppatore per firmare la distribuzione. Anche se il cliente può firmare il manifesto della distribuzione usando strumenti disponibili gratuitamente con .NET Framework SDK, questa operazione potrebbe richiedere una conoscenza più tecnica di quanto il cliente sia disposto o in grado di fornire. In questi casi, lo sviluppatore crea in genere un'applicazione, un sito Web o un altro meccanismo tramite il quale il cliente può inviare la propria versione dell'applicazione per la firma.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Impatto dell'accesso dei clienti alla ClickOnce delle applicazioni
 Anche se lo sviluppatore e il cliente accettano che il cliente debba firmare il manifesto dell'applicazione, ciò genera altri problemi che circondano l'identità dell'applicazione, in particolare in quanto si applica alla distribuzione di applicazioni attendibili. Per altre informazioni su questa funzionalità, vedere Panoramica [della distribuzione di applicazioni attendibili.](../deployment/trusted-application-deployment-overview.md) Si noti che Adventure Works vuole configurare i computer client in modo che qualsiasi applicazione fornita da Microsoft Corporation venga eseguita con attendibilità totale. Se Adventure Works firma il manifesto della distribuzione, ClickOnce userà la firma di sicurezza di Adventure Work per determinare il livello di attendibilità dell'applicazione.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Creare distribuzioni dei clienti usando il manifesto dell'applicazione per l'attendibilità
 ClickOnce in .NET Framework 3.5 contiene una nuova funzionalità che offre a sviluppatori e clienti una nuova soluzione per lo scenario di firma dei manifesti. Il ClickOnce dell'applicazione supporta un nuovo elemento denominato che consente a uno sviluppatore di indicare che la firma digitale del manifesto dell'applicazione è quella che deve essere usata per prendere decisioni di `<useManifestForTrust>` attendibilità. Lo sviluppatore usa strumenti per la creazione di pacchetti di *ClickOnce,* ad esempioMage.exe, *MageUI.exe* e Visual Studio, per includere questo elemento nel manifesto dell'applicazione, nonché per incorporare sia il nome Publisher che il nome dell'applicazione nel manifesto.

 Quando si usa , il manifesto della distribuzione non deve essere firmato `<useManifestForTrust>` con un certificato Authenticode emesso da un'autorità di certificazione. Al contrario, può essere firmato con un certificato autofirmato. Un certificato autofirmato viene generato dal cliente o dallo sviluppatore usando gli strumenti standard di .NET Framework SDK e quindi applicato al manifesto della distribuzione usando gli strumenti di distribuzione ClickOnce standard. Per altre informazioni, vedere [MakeCert.](/windows/desktop/SecCrypto/makecert)

 L'uso di un certificato autofirmato per il manifesto della distribuzione presenta diversi vantaggi. Eliminando la necessità per il cliente di ottenere o creare il proprio certificato Authenticode, semplifica la distribuzione per il cliente, consentendo allo sviluppatore di mantenere la propria identità di personalizzazione `<useManifestForTrust>` nell'applicazione. Il risultato è un set di distribuzioni firmate più sicure e con identità univoche dell'applicazione. In questo modo si elimina il potenziale conflitto che può verificarsi dalla distribuzione della stessa applicazione a più clienti.

 Per informazioni dettagliate su come creare una distribuzione di ClickOnce con abilitato, vedere Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce che non richiede una nuova firma e che mantiene le informazioni sulla `<useManifestForTrust>` personalizzazione. [](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione
 Per comprendere meglio il funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione, si consideri l'esempio seguente. Microsoft ClickOnce un'applicazione .NET Framework 3.5 come destinazione. Il manifesto dell'applicazione `<useManifestForTrust>` usa l'elemento ed è firmato da Microsoft. Adventure Works firma il manifesto della distribuzione usando un certificato autofirmato. I client Adventure Works sono configurati per considerare attendibile qualsiasi applicazione firmata da Microsoft.

 Quando un utente fa clic su un collegamento al manifesto della distribuzione, ClickOnce installa l'applicazione nel computer dell'utente. Le informazioni sul certificato e sulla distribuzione identificano l'applicazione in modo univoco ClickOnce nel computer client. Se l'utente tenta di installare nuovamente la stessa applicazione da un percorso diverso, ClickOnce possibile usare questa identità per determinare che l'applicazione esiste già nel client.

 Successivamente, ClickOnce esamina il certificato Authenticode usato per firmare il manifesto dell'applicazione, che determina il livello di attendibilità ClickOnce verrà concesso. Poiché Adventure Works ha configurato i client in modo da considerare attendibile qualsiasi applicazione firmata da Microsoft, a ClickOnce'applicazione viene concessa l'attendibilità totale. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Creare distribuzioni dei clienti per le versioni precedenti
 Cosa succede se uno sviluppatore distribuisce ClickOnce applicazioni ai clienti che usano versioni precedenti del .NET Framework? Le sezioni seguenti riepilogano diverse soluzioni consigliate, con i vantaggi e gli svantaggi di ognuna.

### <a name="sign-deployments-on-behalf-of-customer"></a>Firmare le distribuzioni per conto del cliente
 Una possibile strategia di distribuzione consiste nel creare un meccanismo per firmare le distribuzioni per conto dei clienti, usando la chiave privata del cliente. Ciò impedisce allo sviluppatore di dover gestire chiavi private o più pacchetti di distribuzione. Lo sviluppatore fornisce semplicemente la stessa distribuzione a ogni cliente. È il cliente a personalizzarlo per il proprio ambiente usando il servizio di firma.

 Uno svantaggio di questo metodo è il tempo e le spese necessari per implementarlo. Anche se un servizio di questo tipo può essere creato usando gli strumenti forniti in .NET Framework SDK, aggiungerà più tempo di sviluppo al ciclo di vita del prodotto.

 Come illustrato in precedenza in questo argomento, un altro svantaggio è che la versione di ogni cliente dell'applicazione avrà la stessa identità dell'applicazione, che potrebbe causare conflitti. Se si tratta di un problema, lo sviluppatore può modificare il campo Nome usato durante la generazione del manifesto della distribuzione per assegnare a ogni applicazione un nome univoco. In questo modo verrà creata un'identità separata per ogni versione dell'applicazione ed eliminati eventuali conflitti di identità potenziali. Questo campo corrisponde all'argomento per Mage.exe e al `-Name` **campo Nome** nella **scheda** Nome MageUI.exe.

 Si supponga, ad esempio, che lo sviluppatore abbia creato un'applicazione denominata Application1. Invece di creare una singola distribuzione con il campo Nome impostato su Application1, lo sviluppatore può creare diverse distribuzioni con una variante specifica del cliente in questo nome, ad esempio Application1-CustomerA, Application1-CustomerB e così via.

### <a name="deploy-using-a-setup-package"></a>Eseguire la distribuzione usando un pacchetto di installazione
 Una seconda possibile strategia di distribuzione consiste nel generare un progetto di installazione Microsoft per eseguire la distribuzione iniziale dell'applicazione ClickOnce distribuzione. Può essere fornito in uno dei diversi formati: come distribuzione MSI, come file eseguibile di installazione (.EXE) o come file CAB (.cab) insieme a uno script batch.

 Usando questa tecnica, lo sviluppatore fornisce al cliente una distribuzione che include i file dell'applicazione, il manifesto dell'applicazione e un manifesto della distribuzione che funge da modello. Il cliente eseguirà il programma di installazione, che richiederebbe un URL di distribuzione (il percorso del server o della condivisione file da cui gli utenti installeranno l'applicazione ClickOnce), nonché un certificato digitale. L'applicazione di installazione può anche scegliere di richiedere ulteriori ClickOnce di configurazione, ad esempio l'intervallo di controllo degli aggiornamenti. Dopo aver raccolto queste informazioni, il programma di installazione genererà il manifesto di distribuzione reale, lo firma e pubblicherà l'applicazione ClickOnce nel percorso del server designato.

 In questa situazione il cliente può firmare il manifesto della distribuzione in tre modi:

1. Il cliente può usare un certificato valido emesso da un'autorità di certificazione (CA).

2. Come variazione in questo approccio, il cliente può scegliere di firmare il manifesto della distribuzione con un certificato autofirmato. Lo svantaggio è che l'applicazione visualizza le parole "Unknown Publisher" quando all'utente viene chiesto se installarla. Tuttavia, il vantaggio è che impedisce ai clienti più piccoli di dover dedicare il tempo e il denaro necessari per un certificato emesso da un'autorità di certificazione.

3. Infine, lo sviluppatore può includere il proprio certificato autofirmato nel pacchetto di installazione. Vengono presentati i potenziali problemi relativi all'identità dell'applicazione descritti in precedenza in questo argomento.

   Lo svantaggio del metodo del progetto di distribuzione di installazione è il tempo e le spese necessari per compilare un'applicazione di distribuzione personalizzata.

### <a name="have-customer-generate-deployment-manifest"></a>Fare in modo che il cliente generi il manifesto della distribuzione
 Una terza strategia di distribuzione possibile consiste nel traslare al cliente solo i file dell'applicazione e il manifesto dell'applicazione. In questo scenario il cliente è responsabile dell'uso dell'SDK .NET Framework per generare e firmare il manifesto della distribuzione.

 Lo svantaggio di questo metodo è che richiede al cliente di installare gli strumenti di .NET Framework SDK e di avere uno sviluppatore o un amministratore di sistema esperto nell'usarli. Alcuni clienti possono richiedere una soluzione che richieda da parte loro un impegno tecnico minimo o nessun impegno tecnico.

## <a name="see-also"></a>Vedi anche
- [Distribuire ClickOnce applicazioni per i server di test e di produzione senza ridistribuire](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e mantiene le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)