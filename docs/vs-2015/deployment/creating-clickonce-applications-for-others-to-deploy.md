---
title: Creazione di applicazioni ClickOnce per altri utenti per la distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: b8f4736066501324d5428fd2634dfacd8c6537a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530403"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Creazione di applicazioni ClickOnce per la distribuzione da parte di terzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creazione di applicazioni ClickOnce per altri utenti su Distribuisci](https://docs.microsoft.com/visualstudio/deployment/creating-clickonce-applications-for-others-to-deploy).  
  
Non tutti gli sviluppatori che creano le distribuzioni di ClickOnce prevede di distribuire le applicazioni stesse. Molti di essi sufficiente includere la loro applicazione con ClickOnce e quindi passare i file a un cliente, ad esempio un'azienda di grandi dimensioni. Il cliente si assume la responsabilità per ospitare l'applicazione nella propria rete. Questo argomento illustra alcuni dei problemi relativi a tali distribuzioni nelle versioni di .NET Framework precedenti alla versione 3.5. Viene quindi illustrata una nuova soluzione fornita utilizzando la nuova funzionalità "Usa manifesto per l'attendibilità" in .NET Framework 3.5. Infine, si conclude con strategie consigliate per la creazione di distribuzioni di ClickOnce per i clienti che ancora usano versioni precedenti di .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemi relativi alla creazione di distribuzioni per i clienti  
 Alcuni problemi si verificano quando si prevede di fornire una distribuzione a un cliente. Il primo problema riguarda la firma del codice. Per poter essere distribuita in una rete, i manifesti di distribuzione e applicazione di una distribuzione di ClickOnce deve essere sia firmati con un certificato digitale. Questo è opportuno quindi chiedersi se usare il certificato dello sviluppatore o un certificato del cliente quando si firma i manifesti.  
  
 È fondamentale, la questione del certificato da usare come identità di un'applicazione ClickOnce è basata sulla firma digitale del manifesto della distribuzione. Se lo sviluppatore si disconnette il manifesto di distribuzione, potrebbe causare conflitti se il cliente è un'azienda di grandi dimensioni e più di una divisione della società consente di distribuire una versione personalizzata dell'applicazione.  
  
 Ad esempio supponga Adventure Works presenta un reparto finanziario e un reparto risorse umane. Entrambi i reparti di licenza applicazione ClickOnce da Microsoft Corporation che genera i report dai dati archiviati in un database SQL. Microsoft fornisce a ogni reparto con una versione dell'applicazione personalizzata per i propri dati. Se le applicazioni sono firmate con lo stesso certificato Authenticode, un utente che tenta di usare entrambe le applicazioni potrebbe verificarsi un errore, come ClickOnce considera la seconda applicazione come identico al primo. In questo caso, il cliente potrebbe subire effetti collaterali imprevisti e indesiderati che includono la perdita di tutti i dati archiviati in locale dall'applicazione.  
  
 Un problema aggiuntivo relativo alla firma del codice è il `deploymentProvider` elemento nel manifesto di distribuzione, che indica la posizione in cui cercare gli aggiornamenti dell'applicazione ClickOnce. Questo elemento è necessario aggiungere al manifesto della distribuzione prima della firma. Se questo elemento viene aggiunto in un secondo momento, il manifesto di distribuzione deve essere firmato di nuovo.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Richiedere il cliente firmare il manifesto di distribuzione  
 Una soluzione al problema delle distribuzioni non univoco consiste nell'avere allo sviluppatore di firmare il manifesto dell'applicazione e il cliente firmare il manifesto della distribuzione. Sebbene questo approccio funzioni, introduce altri problemi. Poiché un certificato Authenticode deve rimanere un asset protetto, il cliente non può solo fornire il certificato per lo sviluppatore per firmare la distribuzione. Mentre il cliente possa firmare il manifesto di distribuzione stessi usando gli strumenti disponibili gratuitamente con .NET Framework SDK, ciò può richiedere conoscenze più tecniche rispetto a cui il cliente è disposto o in grado di fornire. In questi casi, lo sviluppatore crea in genere un'applicazione, sito Web o altro meccanismo attraverso il quale il cliente può inviare la propria versione dell'applicazione per la firma.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>L'impatto del cliente di firma per le applicazioni ClickOnce  
 Anche se lo sviluppatore e il cliente accetta che il cliente deve firmare il manifesto dell'applicazione, questa genera altri problemi che racchiudono l'identità dell'applicazione, soprattutto quando si applica alla distribuzione di applicazioni attendibili. (Per altre informazioni su questa funzionalità, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Si supponga che Adventure Works desidera configurare per i computer client in modo che qualsiasi applicazione fornito da Microsoft Corporation viene eseguito con attendibilità totale. Se Adventure Works si disconnette il manifesto di distribuzione, ClickOnce utilizzerà la firma di sicurezza Adventure Work per determinare il livello di attendibilità dell'applicazione.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Creazione di distribuzioni dei clienti tramite manifesto dell'applicazione per la relazione di Trust  
 ClickOnce di .NET Framework 3.5 contiene una nuova funzionalità che offre agli sviluppatori e ai clienti una nuova soluzione per lo scenario del modo in cui devono essere firmati i manifesti. Il manifesto dell'applicazione ClickOnce supporta un nuovo elemento denominato `<useManifestForTrust>` che consente a uno sviluppatore sta a indicare che la firma digitale del manifesto dell'applicazione è ciò che deve essere utilizzato per prendere decisioni di attendibilità. Lo sviluppatore Usa gli strumenti di creazione del pacchetto ClickOnce, quali Mage.exe, MageUI.exe e Visual Studio, includere l'elemento nel manifesto dell'applicazione, nonché di incorporare i server di pubblicazione sia il nome dell'applicazione nel manifesto.  
  
 Quando si usa `<useManifestForTrust>`, il manifesto di distribuzione non deve essere firmato con un certificato Authenticode emesso da un'autorità di certificazione. In alternativa, possono essere firmato con ciò che è noto come un certificato autofirmato. Un certificato autofirmato generato dal cliente o lo sviluppatore tramite gli strumenti standard di .NET Framework SDK e quindi applicato al manifesto di distribuzione usando gli strumenti di distribuzione standard di ClickOnce. Per altre informazioni, vedere [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Usando un certificato autofirmato per il manifesto di distribuzione presenta diversi vantaggi. Eliminando la necessità del cliente di ottenere o creare il proprio certificato Authenticode, `<useManifestForTrust>` semplifica la distribuzione per il cliente, consentendo agli sviluppatori di gestire la propria identità personalizzazione nell'applicazione. Il risultato è un set di distribuzioni con segno che sono più sicure e dispongono di identità di applicazione univoco. Ciò consente di eliminare il conflitto potenziale può essere generata dalla distribuzione della stessa applicazione a più clienti.  
  
 Per informazioni dettagliate su come creare una distribuzione di ClickOnce con `<useManifestForTrust>` abilitata, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che viene non richiedono nuova firma e che mantiene informazioni sulla personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Manifesto dell'applicazione come per l'attendibilità in fase di esecuzione  
 Per ottenere una migliore comprensione del funzionamento usando il manifesto dell'applicazione per la relazione di trust in fase di esecuzione, si consideri l'esempio seguente. Un'applicazione ClickOnce destinata a .NET Framework 3.5 è stata creata da Microsoft. Il manifesto dell'applicazione usa il `<useManifestForTrust>` elemento e viene firmato da Microsoft. Adventure Works consente di firmare il manifesto di distribuzione usando un certificato autofirmato. Adventure Works sono configurati per considerare attendibili tutte le applicazioni firmate da Microsoft.  
  
 Quando un utente fa clic su un collegamento al manifesto della distribuzione, ClickOnce installa l'applicazione nei computer dell'utente. I certificato e informazioni sulla distribuzione identificare in modo univoco l'applicazione ClickOnce nel computer client. Se l'utente prova a installare di nuovo la stessa applicazione da un percorso diverso, ClickOnce è possibile usare questa identità per stabilire che l'applicazione esiste già nel client.  
  
 Successivamente, ClickOnce esamina il certificato Authenticode utilizzato per firmare il manifesto dell'applicazione, che determina il livello di attendibilità da concedere. Poiché Adventure Works è stato configurato il client per considerare attendibili tutte le applicazioni firmate da Microsoft, l'applicazione ClickOnce viene concessa l'attendibilità. Per altre informazioni, vedere [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Creazione di distribuzioni dei clienti per le versioni precedenti  
 Cosa accade se uno sviluppatore è la distribuzione di applicazioni ClickOnce per i clienti che usano versioni precedenti di .NET Framework? Le sezioni seguenti riepilogano diverse soluzioni consigliate, insieme ai vantaggi e svantaggi di ognuno.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Distribuzioni di accesso per conto dei clienti  
 Una strategia di distribuzione possibili è per gli sviluppatori creare un meccanismo per firmare le distribuzioni per conto dei clienti, usando la chiave privata del cliente. Ciò impedisce lo sviluppatore di dover gestire le chiavi private o più pacchetti di distribuzione. Lo sviluppatore fornisce solo nella stessa distribuzione per ogni cliente. È responsabilità del cliente per personalizzarlo per il proprio ambiente usando il servizio di firma.  
  
 Uno svantaggio di questo metodo è il tempo o spendere denaro necessari per l'implementazione. Anche se tale servizio può essere compilato usando gli strumenti disponibili in .NET Framework SDK, verranno aggiunti più tempo di sviluppo al ciclo di vita del prodotto.  
  
 Come indicato in precedenza in questo argomento, un altro svantaggio è che la versione di ogni cliente dell'applicazione avrà la stessa identità di applicazione, che può causare conflitti. Se si tratta di un problema, lo sviluppatore può modificare il campo Nome usato durante la generazione del manifesto di distribuzione per assegnare un nome univoco a ogni applicazione. Verrà creata un'identità separata per ogni versione dell'applicazione ed eliminare possibili conflitti di identità. Questo campo corrisponde al `-Name` argomento per Mage.exe e per il **Name** campo il **nome** scheda MageUI.exe.  
  
 Ad esempio supponga che lo sviluppatore ha creato un'applicazione denominata Application1. Anziché creare un'unica distribuzione con il campo nome impostato su Application1, lo sviluppatore può creare diverse distribuzioni con questo nome, ad esempio Application1-ClienteA, Application1-ClienteB, presenta una variazione specifiche del cliente e così via.  
  
### <a name="deploy-using-a-setup-package"></a>Eseguire la distribuzione usando un pacchetto di installazione  
 Una strategia di distribuzione possibili secondo consiste nel generare un progetto Microsoft Setup per eseguire la distribuzione iniziale dell'applicazione ClickOnce. Ciò può essere fornito in uno dei diversi formati: come distribuzioni MSI, come un programma di installazione eseguibile (. Con estensione EXE), o come un file cabinet (CAB) insieme a uno script batch.  
  
 Utilizzando questa tecnica, lo sviluppatore fornisce al cliente una distribuzione che include i file dell'applicazione, il manifesto dell'applicazione e un manifesto di distribuzione che funge da modello. Il cliente esegue il programma di installazione, verrà loro richiesto per un URL di distribuzione (il server o condivisione percorso da cui gli utenti installeranno l'applicazione ClickOnce file), oltre a un certificato digitale. L'applicazione di installazione può anche scegliere di richiedere ulteriori opzioni di configurazione di ClickOnce, ad esempio intervallo di controllo di aggiornamento. Dopo che queste informazioni vengono raccolte, il programma di installazione potrebbe generare il manifesto di distribuzione reale, firmarlo e pubblicare l'applicazione ClickOnce per il percorso del server designato.  
  
 Esistono tre modi che il cliente possa firmare il manifesto di distribuzione in questa situazione:  
  
1.  Il cliente può usare un certificato valido emesso da un'autorità di certificazione (CA).  
  
2.  Una variante di questo approccio, il cliente può scegliere di firmare il manifesto della distribuzione con un certificato autofirmato. Lo svantaggio è che causerà l'applicazione visualizzare le parole "Autore sconosciuto" quando l'utente viene richiesto se si desidera installarlo. Tuttavia, il vantaggio è che impedisce ai clienti più piccoli di dover spendere tempo e denaro richiesto per un certificato emesso da un'autorità di certificazione.  
  
3.  Infine, lo sviluppatore può includere il proprio certificato autofirmato nel pacchetto di installazione. Introduce i potenziali problemi con identità di applicazione illustrati in precedenza in questo argomento.  
  
 Lo svantaggio per il metodo di installazione distribuzione progetto è il tempo e denaro normalmente necessario per compilare un'applicazione di distribuzione personalizzato.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Avere cliente Genera manifesto di distribuzione  
 Una terza strategia di distribuzione possibili è per presentare solo i file dell'applicazione e dell'applicazione disattivata al cliente. In questo scenario, il cliente è responsabile dell'uso di .NET Framework SDK per generare e firmare il manifesto della distribuzione.  
  
 Lo svantaggio di questo metodo è che richiede il cliente per installare gli strumenti di .NET Framework SDK e disporre di uno sviluppatore o amministratore di sistema che è utilizzarli. Alcuni clienti potrebbero richiedere una soluzione che richiede poco o nessun impegno tecnico parte loro.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di applicazioni ClickOnce per i test e i server di produzione senza riapposizione della firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Procedura dettagliata: distribuzione manuale di una applicazione ClickOnce che non richiede una nuova firma e mantiene le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)



