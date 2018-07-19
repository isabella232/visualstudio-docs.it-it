---
title: Distribuzione di applicazioni ClickOnce per i test e i server di produzione senza riapposizione della firma | Microsoft Docs
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
ms.openlocfilehash: bb8e84397a5c08a00b704bc571ca1eba3361bfd6
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081397"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuire le applicazioni ClickOnce per i server di test e produzione senza riapposizione della firma
Questo articolo illustra una funzionalità introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce dalla più percorsi di rete senza riapposizione della firma o la modifica di ClickOnce manifesti ClickOnce.  
  
> [!NOTE]
>  Riapposizione della firma è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Se possibile, usare questo metodo. Per altre informazioni, vedere [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
 Gli sviluppatori di terze parti e fornitori di software indipendenti possono optare per questa funzionalità, rendendo più semplice per i clienti aggiornare le proprie applicazioni. Questa funzionalità può essere utilizzata nelle situazioni seguenti:  
  
-   Quando si aggiorna un'applicazione, non per la prima installazione di un'applicazione.  
  
-   Quando è presente solo una configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata in modo da puntare a due database diversi, non è possibile utilizzare questa funzionalità.  
  
## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Escludere deploymentProvider da manifesti di distribuzione  
 In .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce che viene installato nel sistema per la disponibilità offline è necessario elencare un `deploymentProvider` nel relativo manifesto di distribuzione. Il `deploymentProvider` è noto anche come percorso di aggiornamento; è il percorso in cui ClickOnce controlla gli aggiornamenti dell'applicazione. Questo requisito, oltre alla necessità per gli autori dell'applicazione firmare le distribuzioni, rendeva difficile per una società per aggiornare un'applicazione ClickOnce da un fornitore o da terze parti. Inoltre rende più difficile distribuire l'applicazione stessa da più posizioni nella stessa rete.  
  
 Con le modifiche apportate alla funzionalità ClickOnce di .NET Framework 3.5, è possibile che terze parti fornire un'applicazione ClickOnce in un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.  
  
 Per poter sfruttare i vantaggi di questa funzionalità, è necessario escludere gli sviluppatori di applicazioni ClickOnce `deploymentProvider` dai manifesti di distribuzione. Questo requisito implica che è necessario escludere il `-providerUrl` argomento quando si crea la distribuzione dei manifesti con Mage.exe. O, se si desidera generare i manifesti di distribuzione con MageUI.exe, è necessario assicurarsi che il **posizione avviare** casella di testo il **manifesto dell'applicazione** scheda viene lasciata vuota.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e applicazione degli aggiornamenti  
 A partire da .NET Framework 3.5, è non è più necessario specificare un `deploymentProvider` nel manifesto della distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo sia online e offline. Questa modifica supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione, ma consente ad altre società distribuire l'applicazione tramite le proprie reti.  
  
 Il punto importante da ricordare è che le applicazioni che escludono una `deploymentProvider` non è possibile modificare il proprio percorso di installazione durante gli aggiornamenti, fino a quando non sono inclusi un aggiornamento che include il `deploymentProvider` tag nuovamente.  
  
 Di seguito sono riportati due esempi per chiarire questo concetto. Nel primo esempio, si pubblica un'applicazione ClickOnce che non ha `deploymentProvider` tag e si chiede agli utenti di installare l'app da http://www.adatum.com/MyApplication/. Se si decide che si desidera pubblicare al successivo aggiornamento dell'applicazione dal http://subdomain.adatum.com/MyApplication/, non esiste alcun modo da utilizzare per indicare questo nel manifesto di distribuzione che si trova in http://www.adatum.com/MyApplication/. È possibile eseguire una delle seguenti operazioni:  
  
-   Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.  
  
-   Includere un aggiornamento sul http://www.adatum.com/MyApplication/ che include un `deploymentProvider` che punta a http://www.adatum.com/MyApplication/. Quindi, rilasciare un altro aggiornamento in un secondo momento con `deploymentProvider` che punta a http://subdomain.adatum.com/MyApplication/.  
  
 Nel secondo esempio, si pubblica un'applicazione ClickOnce che specifica `deploymentProvider`, e si decide quindi di rimuoverlo. Una volta nella nuova versione senza `deploymentProvider` viene scaricato ai client, non è possibile reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione che ha `deploymentProvider` ripristinato. Come con il primo esempio `deploymentProvider` inizialmente deve puntare al percorso di aggiornamento corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un `deploymentProvider` che fa riferimento a http://subdomain.adatum.com/MyApplication/, al successivo aggiornamento ha esito negativo.  
  
## <a name="create-a-deployment"></a>Creare una distribuzione  
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da diversi percorsi di rete, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e conserva le informazioni di personalizzazione](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).  
  
## <a name="see-also"></a>Vedere anche  
 [*Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [*MageUI.exe* (Manifest Generation and Editing Tool, Client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)