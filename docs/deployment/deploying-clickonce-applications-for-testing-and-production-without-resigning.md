---
title: Distribuire ClickOnce app senza dover firmare di nuovo
description: Informazioni sulla distribuzione ClickOnce applicazioni da più percorsi di rete senza firmare di nuovo o modificare ClickOnce manifesti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: ca7c1e4e8e56708a529eb23f68b9ab7bc3e3530cdd0b39e4b358a3b435da3810
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435673"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuire ClickOnce applicazioni per i server di test e di produzione senza ridistribuire
Questo articolo descrive una funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più percorsi di rete senza firmare nuovamente o modificare i manifesti ClickOnce.

> [!NOTE]
> La rinuncia è ancora il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Quando possibile, usare il metodo di rimozione. Per altre informazioni, vedere [*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Gli sviluppatori di terze parti e gli ISV possono acconsentire esplicitamente a questa funzionalità, semplificando l'aggiornamento delle applicazioni da parte dei clienti. Questa funzionalità può essere usata nelle situazioni seguenti:

- Quando si aggiorna un'applicazione, non per la prima installazione di un'applicazione.

- Quando è presente una sola configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, non è possibile usare questa funzionalità.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Escludere deploymentProvider dai manifesti della distribuzione
 Nelle .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce installata nel sistema per la disponibilità offline deve elencare un nel manifesto della `deploymentProvider` distribuzione. Viene spesso indicato come percorso di aggiornamento, ma è il percorso in cui ClickOnce `deploymentProvider` gli aggiornamenti dell'applicazione. Questo requisito, insieme alla necessità per gli editori di applicazioni di firmare le proprie distribuzioni, ha reso difficile per un'azienda aggiornare un'applicazione ClickOnce da un fornitore o da terze parti. Rende inoltre più difficile distribuire la stessa applicazione da più posizioni nella stessa rete.

 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile che terze parti forniranno un'applicazione ClickOnce a un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.

 Per sfruttare questa funzionalità, gli sviluppatori di applicazioni ClickOnce devono escludere `deploymentProvider` dai manifesti di distribuzione. Questo requisito significa che è necessario escludere `-providerUrl` l'argomento quando si creano manifesti di distribuzione con Mage.exe. In caso contrario, se si generano manifesti di distribuzione  con MageUI.exe, è  necessario assicurarsi che la casella di testo Posizione di avvio nella scheda Manifesto dell'applicazione sia lasciata vuota.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e aggiornamenti dell'applicazione
 A partire da .NET Framework 3.5, non è più necessario specificare un nel manifesto della distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo online e `deploymentProvider` offline. Questa modifica supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione manualmente, ma consentire ad altre società di distribuire l'applicazione nelle proprie reti.

 L'aspetto importante da ricordare è che le applicazioni che escludono non possono modificare il percorso di installazione durante gli aggiornamenti, fino a quando non viene nuovamente prodotto un aggiornamento che `deploymentProvider` `deploymentProvider` include il tag .

 Ecco due esempi per chiarire questo punto. Nel primo esempio si pubblica un'applicazione ClickOnce senza tag e si chiede agli utenti di `deploymentProvider` installarla da `http://www.adatum.com/MyApplication/` . Se si decide di pubblicare l'aggiornamento successivo dell'applicazione da , non è possibile indicarlo nel manifesto della distribuzione `http://subdomain.adatum.com/MyApplication/` che risiede in `http://www.adatum.com/MyApplication/` . È possibile eseguire una delle due operazioni seguenti:

- Indicare agli utenti di disinstallare la versione precedente e installare la nuova versione dal nuovo percorso.

- Includere un aggiornamento in `http://www.adatum.com/MyApplication/` che include un che punta a `deploymentProvider` `http://www.adatum.com/MyApplication/` . Rilasciare quindi un altro aggiornamento in un secondo momento `deploymentProvider` con che punta a `http://subdomain.adatum.com/MyApplication/` .

  Nel secondo esempio si pubblica un'ClickOnce che specifica `deploymentProvider` e quindi si decide di rimuoverla. Dopo che la nuova versione senza è stata scaricata nei client, non è possibile reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione `deploymentProvider` dell'applicazione `deploymentProvider` ripristinata. Come nel primo esempio, deve puntare inizialmente al percorso di aggiornamento `deploymentProvider` corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un oggetto che fa riferimento a `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` , l'aggiornamento successivo non riesce.

## <a name="create-a-deployment"></a>Creare una distribuzione
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da percorsi di rete diversi, vedere Procedura [dettagliata:](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)Distribuire manualmente un'applicazione ClickOnce che non richiede una nuova firma e che mantiene le informazioni sulla personalizzazione.

## <a name="see-also"></a>Vedi anche
- [*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
