---
title: Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza dimissioni Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395377"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza riapposizione della firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrata una nuova funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più percorsi di rete senza firmare nuovamente o modificare i manifesti ClickOnce.  
  
> [!NOTE]
> La riassegnazione è ancora il metodo preferito per la distribuzione di nuove versioni di applicazioni. Quando possibile, utilizzare il metodo di dimissioni. Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Gli sviluppatori di terze parti e gli ISV possono acconsentire esplicitamente a questa funzionalità, semplificando l'aggiornamento delle applicazioni da parte dei clienti. Questa funzione può essere utilizzata nelle seguenti situazioni:  
  
- Quando si aggiorna un'applicazione, non la prima installazione di un'applicazione.  
  
- Quando è presente una sola configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, non è possibile utilizzare questa funzionalità.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Esclusione di deploymentProvider dai manifesti di distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0 qualsiasi applicazione ClickOnce installata nel `deploymentProvider` sistema per la disponibilità offline deve specificare un nel manifesto di distribuzione. Il `deploymentProvider` è spesso indicato come il percorso di aggiornamento; è il percorso in cui ClickOnceClickOnce controllerà gli aggiornamenti dell'applicazione. Questo requisito, unito alla necessità per gli editori di applicazioni di firmare le proprie distribuzioni, rendeva difficile per una società aggiornare un'applicazione ClickOnce da un fornitore o da un'altra terza parte. Rende inoltre più difficile distribuire la stessa applicazione da più posizioni nella stessa rete.  
  
 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile per una terza parte fornire un'applicazione ClickOnce a un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.  
  
 Per sfruttare questa funzionalità, gli sviluppatori di `deploymentProvider` applicazioni ClickOnce Devono escludere dai manifesti di distribuzione. Ciò significa `-providerUrl` escludere l'argomento quando si creano manifesti di distribuzione con Mage.exe o assicurarsi che la casella di testo Percorso di **avvio** nella scheda **Manifesto dell'applicazione** sia lasciata vuota se si generano manifesti di distribuzione con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e aggiornamenti dell'applicazione  
 A partire da .NET Framework 3.5, non `deploymentProvider` è più necessario specificare un nel manifesto di distribuzione per distribuire un'applicazione ClickOnce sia per l'utilizzo online che offline. Questo supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione manualmente, ma consentire ad altre aziende di distribuire l'applicazione sulle proprie reti.  
  
 Il punto chiave da ricordare `deploymentProvider` è che le applicazioni che escludono un `deploymentProvider` non può modificare il percorso di installazione durante gli aggiornamenti, fino a quando non forniscono nuovamente un aggiornamento che include nuovamente il tag.  
  
 Ecco due esempi per chiarire questo punto. Nel primo esempio si pubblica un'applicazione `deploymentProvider` ClickOnce senza tag e si `http://www.adatum.com/MyApplication/`chiede agli utenti di installarla da . Se si decide di pubblicare il successivo `http://subdomain.adatum.com/MyApplication/`aggiornamento dell'applicazione da , non sarà possibile digitarlo nel manifesto di distribuzione che risiede in `http://www.adatum.com/MyApplication/`. È possibile eseguire una delle due operazioni seguenti:  
  
- Comunicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.  
  
- Includere un `http://www.adatum.com/MyApplication/` aggiornamento che `deploymentProvider` include `http://www.adatum.com/MyApplication/`un che punta a . Quindi, rilasciare un `deploymentProvider` altro aggiornamento `http://subdomain.adatum.com/MyApplication/`in un secondo momento con il punto di .  
  
  Nel secondo esempio si pubblica un'applicazione `deploymentProvider`ClickOnce che specifica e si decide quindi di rimuoverla. Una volta scaricata la nuova versione senza `deploymentProvider` che sia stata scaricata nei client, non sarà `deploymentProvider` possibile reindirizzare il percorso utilizzato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione ripristinata. Come nel primo `deploymentProvider` esempio, deve inizialmente puntare alla posizione di aggiornamento corrente, non alla nuova posizione. In questo caso, se si `deploymentProvider` tenta `http://subdomain.adatum.com/MyApplication/`di inserire un che fa riferimento a , l'aggiornamento successivo avrà esito negativo.  
  
## <a name="creating-a-deployment"></a>Creazione di una distribuzioneCreating a Deployment  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da percorsi di rete diversi, vedere [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)la firma in più e che mantiene le informazioni di personalizzazione .  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (strumento di generazione e modifica di manifesti, client grafico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
