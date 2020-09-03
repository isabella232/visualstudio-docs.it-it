---
title: Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza firma | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395377"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza riapposizione della firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrata una nuova funzionalità di ClickOnce introdotta nella .NET Framework versione 3,5 che consente la distribuzione di applicazioni ClickOnce da più percorsi di rete senza ripetere la firma o la modifica dei manifesti ClickOnce.  
  
> [!NOTE]
> La firma è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Quando possibile, usare il metodo di firma. Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Gli sviluppatori e gli ISV di terze parti possono acconsentire esplicitamente a questa funzionalità, rendendo più semplice per i clienti aggiornare le proprie applicazioni. Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
- Quando si aggiorna un'applicazione, non la prima installazione di un'applicazione.  
  
- Quando è presente una sola configurazione dell'applicazione in un computer. Se, ad esempio, un'applicazione è configurata in modo da puntare a due database diversi, non è possibile utilizzare questa funzionalità.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Esclusione di deploymentProvider dai manifesti di distribuzione  
 Nel .NET Framework 2,0 e .NET Framework 3,0, qualsiasi applicazione ClickOnce installata nel sistema per la disponibilità offline deve specificare un `deploymentProvider` nel manifesto di distribuzione. `deploymentProvider`Viene spesso definito percorso di aggiornamento, ovvero il percorso in cui ClickOnce verificherà gli aggiornamenti dell'applicazione. Questo requisito, associato alla necessità per gli editori di applicazioni di firmare le distribuzioni, rendeva difficile per un'azienda aggiornare un'applicazione ClickOnce da un fornitore o da terze parti. Rende inoltre più difficile distribuire la stessa applicazione da più posizioni nella stessa rete.  
  
 Con le modifiche apportate a ClickOnce nella .NET Framework 3,5, è possibile che una terza parte fornisca un'applicazione ClickOnce a un'altra organizzazione, in modo da poter distribuire l'applicazione nella propria rete.  
  
 Per sfruttare i vantaggi di questa funzionalità, gli sviluppatori di applicazioni ClickOnce devono escludere `deploymentProvider` dai rispettivi manifesti di distribuzione. Questo significa escludere l' `-providerUrl` argomento quando si creano manifesti di distribuzione con Mage.exe o assicurarsi che la casella di testo **percorso di avvio** nella scheda **manifesto dell'applicazione** venga lasciata vuota se si generano manifesti di distribuzione con MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>Aggiornamenti di deploymentProvider e delle applicazioni  
 A partire da .NET Framework 3,5, non è più necessario specificare un `deploymentProvider` nel manifesto di distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo in linea e non in linea. Questo supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione autonomamente, ma consentire ad altre aziende di distribuire l'applicazione attraverso le reti.  
  
 Il punto chiave da ricordare è che le applicazioni che escludono un `deploymentProvider` non possono modificare il percorso di installazione durante gli aggiornamenti, fino a quando non vengono forniti un aggiornamento che include di `deploymentProvider` nuovo il tag.  
  
 Ecco due esempi per chiarire questo aspetto. Nel primo esempio si pubblica un'applicazione ClickOnce senza `deploymentProvider` tag e si chiede agli utenti di installarla da `http://www.adatum.com/MyApplication/` . Se si decide di voler pubblicare il successivo aggiornamento dell'applicazione da `http://subdomain.adatum.com/MyApplication/` , non sarà possibile significare questo nel manifesto di distribuzione che risiede in `http://www.adatum.com/MyApplication/` . È possibile eseguire una delle due operazioni seguenti:  
  
- Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dal nuovo percorso.  
  
- Includere un aggiornamento in `http://www.adatum.com/MyApplication/` che includa un oggetto che `deploymentProvider` punta a `http://www.adatum.com/MyApplication/` . Rilasciare quindi un altro aggiornamento in un secondo momento con il `deploymentProvider` puntatore a `http://subdomain.adatum.com/MyApplication/` .  
  
  Nel secondo esempio si pubblica un'applicazione ClickOnce che specifica `deploymentProvider` e si decide di rimuoverla. Una volta che la nuova versione non `deploymentProvider` è stata scaricata nei client, non sarà possibile reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione `deploymentProvider` ripristinata. Come nel primo esempio, `deploymentProvider` deve puntare inizialmente al percorso di aggiornamento corrente, non alla nuova posizione. In questo caso, se si tenta di inserire un oggetto `deploymentProvider` che fa riferimento a `http://subdomain.adatum.com/MyApplication/` , il prossimo aggiornamento avrà esito negativo.  
  
## <a name="creating-a-deployment"></a>Creazione di una distribuzione  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da percorsi di rete diversi, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e che conserva le informazioni di personalizzazione](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
