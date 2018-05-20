---
title: Distribuzione di applicazioni ClickOnce per il test e i server di produzione senza riapposizione della firma | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57b4761ed7f0b223e459fc1ac77ad93c546e02dc
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuzione di applicazioni ClickOnce per i server di test e di produzione senza riapposizione della firma
Questo articolo descrive una funzionalità introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più posizioni di rete senza riapposizione della firma o la modifica di ClickOnce manifesti ClickOnce.  
  
> [!NOTE]
>  Riapposizione della firma è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Quando possibile, utilizzare questo metodo. Per altre informazioni, vedere [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Gli sviluppatori di terze parti e gli ISV possono optare per questa funzionalità, rendendo più semplice per i loro clienti aggiornare le proprie applicazioni. Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
-   Quando si aggiorna un'applicazione, non per la prima installazione di un'applicazione.  
  
-   Quando si verifica solo una configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, è possibile utilizzare questa funzionalità.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Esclusione di deploymentProvider dai manifesti della distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0, è necessario elencare qualsiasi applicazione ClickOnce che viene installato nel sistema per la disponibilità offline un `deploymentProvider` nel manifesto di distribuzione. Il `deploymentProvider` è noto anche come percorso di aggiornamento; è il percorso in cui ClickOnce Cerca gli aggiornamenti dell'applicazione. Questo requisito, con la necessità di server di pubblicazione dell'applicazione firmare le distribuzioni, rende difficile per un'azienda per aggiornare un'applicazione ClickOnce da un fornitore o da terze parti. Inoltre rende più difficile distribuire l'applicazione stessa da più posizioni nella stessa rete.  
  
 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile per una terza parte per fornire un'applicazione ClickOnce in un'altra organizzazione, che è quindi possibile distribuire l'applicazione su una propria rete.  
  
 Per sfruttare i vantaggi di questa funzionalità, è necessario escludere gli sviluppatori di applicazioni ClickOnce `deploymentProvider` dai manifesti di distribuzione. Questo requisito significa che è necessario escludere il `-providerUrl` argomento quando si crea la distribuzione di manifesti con Mage.exe. O, se si siano generando manifesti di distribuzione con MageUI.exe, è necessario assicurarsi che il **avviare percorso** casella di testo al **Application Manifest** scheda viene lasciata vuota.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e gli aggiornamenti dell'applicazione  
 A partire da .NET Framework 3.5, non è necessario specificare un `deploymentProvider` nel manifesto di distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo online e offline. Questa modifica supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione, ma consente ad altre società distribuire l'applicazione su reti.  
  
 L'aspetto importante da ricordare è che le applicazioni che escludono una `deploymentProvider` non è possibile modificare il proprio percorso di installazione durante gli aggiornamenti, fino a che forniscono un aggiornamento che include il `deploymentProvider` tag nuovamente.  
  
 Di seguito sono riportati due esempi per chiarire questo concetto. Nel primo esempio, si pubblica un'applicazione ClickOnce che non ha alcun `deploymentProvider` tag e si chiede agli utenti di installarla da http://www.adatum.com/MyApplication/. Se si decide che si desidera pubblicare il successivo aggiornamento dell'applicazione dal http://subdomain.adatum.com/MyApplication/, è non necessario indicare questo nel manifesto di distribuzione che risiede in alcun modo http://www.adatum.com/MyApplication/. È possibile eseguire una delle seguenti operazioni:  
  
-   Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.  
  
-   Includere un aggiornamento sul http://www.adatum.com/MyApplication/ che include un `deploymentProvider` che punta a http://www.adatum.com/MyApplication/. Infine, rilasciare un altro aggiornamento in un secondo momento con `deploymentProvider` che punta a http://subdomain.adatum.com/MyApplication/.  
  
 Nel secondo esempio, si pubblica un'applicazione ClickOnce che specifica `deploymentProvider`, e si decide quindi di rimuoverlo. Una volta la nuova versione senza `deploymentProvider` viene scaricato ai client, non è possibile reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione che ha `deploymentProvider` ripristinato. Come con il primo esempio `deploymentProvider` inizialmente deve puntare al percorso di aggiornamento corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un `deploymentProvider` che fa riferimento a http://subdomain.adatum.com/MyApplication/, al successivo aggiornamento avrà esito negativo.  
  
## <a name="creating-a-deployment"></a>Creazione di una distribuzione  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da diversi percorsi di rete, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che Does non richiedono nuova firma e che mantiene informazioni sulla personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)