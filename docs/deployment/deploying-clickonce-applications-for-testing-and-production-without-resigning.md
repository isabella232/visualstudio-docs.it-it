---
title: Distribuire ClickOnce app senza una firma di nuovo
description: Informazioni sulla distribuzione di ClickOnce applicazioni da più percorsi di rete senza firmare di nuovo o modificare ClickOnce manifesti.
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
ms.openlocfilehash: 19eb91f9becdeeddbf5f5436a4f0b3b7da59da77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160855"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuire ClickOnce applicazioni per i server di test e di produzione senza dimettersi
Questo articolo descrive una funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più percorsi di rete senza firmare di nuovo o modificare i manifesti ClickOnce.

> [!NOTE]
> La disdezione è comunque il metodo preferito per la distribuzione di nuove versioni delle applicazioni. Quando possibile, usare il metodo di ritiro. Per altre informazioni, vedere [*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Gli sviluppatori di terze parti e gli ISV possono acconsentire esplicitamente a questa funzionalità, semplificando l'aggiornamento delle applicazioni da parte dei clienti. Questa funzionalità può essere usata nelle situazioni seguenti:

- Quando si aggiorna un'applicazione, non per la prima installazione di un'applicazione.

- Quando è presente una sola configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, non è possibile usare questa funzionalità.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Escludere deploymentProvider dai manifesti di distribuzione
 Nelle .NET Framework 2.0 e .NET Framework 3.0, qualsiasi applicazione ClickOnce installata nel sistema per la disponibilità offline deve elencare un nel manifesto della `deploymentProvider` distribuzione. L'oggetto viene spesso definito percorso di aggiornamento, ma è il percorso in cui ClickOnce `deploymentProvider` gli aggiornamenti dell'applicazione. Questo requisito, insieme alla necessità che gli editori di applicazioni firmano le proprie distribuzioni, rendeva difficile per un'azienda aggiornare un'applicazione ClickOnce da un fornitore o da altre terze parti. Rende anche più difficile distribuire la stessa applicazione da più posizioni nella stessa rete.

 Con le modifiche apportate a ClickOnce nel .NET Framework 3.5, è possibile che terze parti forniranno un'applicazione ClickOnce a un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.

 Per sfruttare questa funzionalità, gli sviluppatori di applicazioni ClickOnce devono escludere `deploymentProvider` dai manifesti di distribuzione. Questo requisito significa che è necessario escludere `-providerUrl` l'argomento quando si creano manifesti di distribuzione con Mage.exe. In caso contrario, se si generano manifesti di distribuzione con  MageUI.exe, è  necessario assicurarsi che la casella di testo Posizione di avvio nella scheda Manifesto dell'applicazione sia lasciata vuota.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e aggiornamenti delle applicazioni
 A partire da .NET Framework 3.5, non è più necessario specificare un nel manifesto della distribuzione per distribuire un'applicazione ClickOnce per l'utilizzo online e `deploymentProvider` offline. Questa modifica supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione manualmente, ma consentire ad altre aziende di distribuire l'applicazione sulle proprie reti.

 Il punto importante da ricordare è che le applicazioni che escludono un non possono modificare il percorso di installazione durante gli aggiornamenti, fino a quando non spediranno un aggiornamento che include di nuovo `deploymentProvider` `deploymentProvider` il tag.

 Ecco due esempi per chiarire questo punto. Nel primo esempio si pubblica un'applicazione ClickOnce senza tag e si chiede agli utenti `deploymentProvider` di installarla da `http://www.adatum.com/MyApplication/` . Se si decide di pubblicare il successivo aggiornamento dell'applicazione da , non è possibile indicarlo nel manifesto di distribuzione che `http://subdomain.adatum.com/MyApplication/` risiede in `http://www.adatum.com/MyApplication/` . È possibile eseguire una delle due operazioni seguenti:

- Indicare agli utenti di disinstallare la versione precedente e di installare la nuova versione dal nuovo percorso.

- Includere un aggiornamento in `http://www.adatum.com/MyApplication/` che include un che punta a `deploymentProvider` `http://www.adatum.com/MyApplication/` . Rilasciare quindi un altro aggiornamento in un secondo momento `deploymentProvider` con che punta a `http://subdomain.adatum.com/MyApplication/` .

  Nel secondo esempio si pubblica un'ClickOnce che specifica e quindi `deploymentProvider` si decide di rimuoverla. Dopo aver scaricato la nuova versione senza nei client, non è possibile reindirizzare il percorso usato per gli aggiornamenti fino a quando non si rilascia una versione `deploymentProvider` dell'applicazione `deploymentProvider` ripristinata. Come nel primo esempio, deve puntare inizialmente al percorso di aggiornamento `deploymentProvider` corrente, non al nuovo percorso. In questo caso, se si tenta di inserire un oggetto che fa riferimento a `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` , l'aggiornamento successivo non riesce.

## <a name="create-a-deployment"></a>Creare una distribuzione
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da percorsi di rete diversi, vedere Procedura [dettagliata:](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)Distribuire manualmente un'applicazione ClickOnce che non richiede la nuova firma e che mantiene le informazioni di personalizzazione.

## <a name="see-also"></a>Vedi anche
- [*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Strumento per la generazione e la modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
