---
title: Distribuzione di applicazioni ClickOnce per i test e i server di produzione senza riapposizione della firma | Microsoft Docs
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
ms.openlocfilehash: c853e24da3f203d67874d7b9740d3239abd78c14
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066598"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza riapposizione della firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento illustra una nuova funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce dalla più percorsi di rete senza riapposizione della firma o la modifica di ClickOnce manifesti.  
  
> [!NOTE]
>  Riapposizione della firma è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Se possibile, usare questo metodo. Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Gli ISV e sviluppatori di terze parti possono acconsentire esplicitamente a questa funzionalità, rendendo più semplice per i clienti aggiornare le applicazioni. Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
- Quando si aggiorna un'applicazione, non la prima installazione di un'applicazione.  
  
- Quando è presente solo una configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata in modo da puntare a due database diversi, non è possibile utilizzare questa funzionalità.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Esclusione deploymentProvider dai manifesti della distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce che viene installato nel sistema per la disponibilità offline è necessario specificare un `deploymentProvider` nel relativo manifesto di distribuzione. Il `deploymentProvider` è noto anche come percorso di aggiornamento; è il percorso in cui ClickOnce controllerà gli aggiornamenti dell'applicazione. Questo requisito, insieme alla necessità per gli autori dell'applicazione firmare le distribuzioni, rendeva difficile per una società per aggiornare un'applicazione ClickOnce da un fornitore o altre terze parti. Inoltre rende più difficile distribuire l'applicazione stessa da più posizioni nella stessa rete.  
  
 Con le modifiche apportate alla funzionalità ClickOnce di .NET Framework 3.5, è possibile che una terza parte fornire un'applicazione ClickOnce in un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.  
  
 Per poter sfruttare i vantaggi di questa funzionalità, è necessario escludere gli sviluppatori di applicazioni ClickOnce `deploymentProvider` dai manifesti di distribuzione. Evitare di includere il `-providerUrl` argomento quando si crea la distribuzione dei manifesti con Mage.exe o assicurandosi che il **avviare posizione** casella di testo il **manifesto dell'applicazione** scheda viene lasciata vuota se è sono la generazione di manifesti di distribuzione con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e gli aggiornamenti dell'applicazione  
 A partire da .NET Framework 3.5, è non è più necessario specificare un `deploymentProvider` nel manifesto della distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo sia online e offline. Supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione, ma consente ad altre società distribuire l'applicazione tramite le proprie reti.  
  
 Il punto principale da ricordare è che le applicazioni che escludono una `deploymentProvider` non è possibile modificare il proprio percorso di installazione durante gli aggiornamenti, fino a quando non sono inclusi un aggiornamento che include il `deploymentProvider` tag nuovamente.  
  
 Di seguito sono riportati due esempi per chiarire questo concetto. Nel primo esempio, si pubblica un'applicazione ClickOnce che non ha `deploymentProvider` tag e si chiede agli utenti di installare l'app da http://www.adatum.com/MyApplication/. Se si decide che si desidera pubblicare al successivo aggiornamento dell'applicazione dal http://subdomain.adatum.com/MyApplication/, è non necessario indicare questo nel manifesto di distribuzione che si trova in alcun modo http://www.adatum.com/MyApplication/. È possibile eseguire una delle seguenti operazioni:  
  
- Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.  
  
- Includere un aggiornamento sul http://www.adatum.com/MyApplication/ che include un `deploymentProvider` che punta a http://www.adatum.com/MyApplication/. Quindi, rilasciare un altro aggiornamento in un secondo momento con `deploymentProvider` che punta a http://subdomain.adatum.com/MyApplication/.  
  
  Nel secondo esempio, si pubblica un'applicazione ClickOnce che specifica `deploymentProvider`, e si decide quindi di rimuoverlo. Una volta nella nuova versione senza `deploymentProvider` è stato scaricato ai client, non sarà in grado di reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione che ha `deploymentProvider` ripristinato. Come con il primo esempio `deploymentProvider` inizialmente deve puntare al percorso di aggiornamento corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un `deploymentProvider` che fa riferimento a http://subdomain.adatum.com/MyApplication/, al successivo aggiornamento avrà esito negativo.  
  
## <a name="creating-a-deployment"></a>Creazione di una distribuzione  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da diversi percorsi di rete, vedere [procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e conserva le informazioni di personalizzazione](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
