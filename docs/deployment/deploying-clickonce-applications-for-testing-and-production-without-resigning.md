---
title: Distribuire app ClickOnce senza firmare nuovamenteDeploy ClickOnce apps without re-signing
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395328"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Distribuire applicazioni ClickOnce per i server di test e produzione senza rassegnare le dimissioniDeploy ClickOnce applications for testing and production servers without resigning
In questo articolo viene descritta una funzionalità di ClickOnce introdotta in .NET Framework versione 3.5 che consente la distribuzione di applicazioni ClickOnce da più percorsi di rete senza firmare nuovamente o modificare i manifesti ClickOnce.

> [!NOTE]
> La riassegnazione è ancora il metodo preferito per la distribuzione di nuove versioni di applicazioni. Quando possibile, utilizzare il metodo di dimissioni. Per altre informazioni, vedere [*Mage.exe* (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Gli sviluppatori di terze parti e gli ISV possono acconsentire esplicitamente a questa funzionalità, semplificando l'aggiornamento delle applicazioni da parte dei clienti. Questa funzione può essere utilizzata nelle seguenti situazioni:

- Quando si aggiorna un'applicazione, non per la prima installazione di un'applicazione.

- Quando è presente una sola configurazione dell'applicazione in un computer. Ad esempio, se un'applicazione è configurata per puntare a due database diversi, non è possibile utilizzare questa funzionalità.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Escludere deploymentProvider dai manifesti di distribuzioneExclude deploymentProvider from deployment manifests
 In .NET Framework 2.0 e .NET Framework 3.0 qualsiasi applicazione ClickOnce installata nel `deploymentProvider` sistema per la disponibilità offline deve elencare un nel manifesto di distribuzione. Il `deploymentProvider` è spesso indicato come il percorso di aggiornamento; è il percorso in cui ClickOnce Controlla gli aggiornamenti dell'applicazione. Questo requisito, insieme alla necessità per gli editori di applicazioni di firmare le proprie distribuzioni, ha reso difficile per una società aggiornare un'applicazione ClickOnce da un fornitore o da un'altra terza parte. Rende inoltre più difficile distribuire la stessa applicazione da più posizioni nella stessa rete.

 Con le modifiche apportate a ClickOnce in .NET Framework 3.5, è possibile per una terza parte fornire un'applicazione ClickOnce a un'altra organizzazione, che può quindi distribuire l'applicazione nella propria rete.

 Per sfruttare questa funzionalità, gli sviluppatori di `deploymentProvider` applicazioni ClickOnce Devono escludere dai manifesti di distribuzione. Questo requisito significa che `-providerUrl` è necessario escludere l'argomento quando si creano manifesti di distribuzione con Mage.exe.This requirement means that you must exclude the argument when you create deployment manifests with Mage.exe. In alternativa, se si generano manifesti di distribuzione con MageUI.exe, è necessario assicurarsi che la casella di testo Percorso di **avvio** nella scheda **Manifesto applicazione** venga lasciata vuota.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider e aggiornamenti dell'applicazione
 A partire da .NET Framework 3.5, non `deploymentProvider` è più necessario specificare un nel manifesto di distribuzione per distribuire un'applicazione ClickOnce sia per l'utilizzo online che offline. Questa modifica supporta lo scenario in cui è necessario creare un pacchetto e firmare la distribuzione manualmente, ma consentire ad altre aziende di distribuire l'applicazione nelle proprie reti.

 Il punto importante da ricordare `deploymentProvider` è che le applicazioni che escludono un `deploymentProvider` non può modificare il percorso di installazione durante gli aggiornamenti, fino a quando non forniscono nuovamente un aggiornamento che include nuovamente il tag.

 Ecco due esempi per chiarire questo punto. Nel primo esempio si pubblica un'applicazione `deploymentProvider` ClickOnce senza tag e si `http://www.adatum.com/MyApplication/`chiede agli utenti di installarla da . Se si decide di pubblicare il successivo `http://subdomain.adatum.com/MyApplication/`aggiornamento dell'applicazione da , non è possibile `http://www.adatum.com/MyApplication/`digitarlo nel manifesto di distribuzione che risiede in . È possibile eseguire una delle due operazioni seguenti:

- Comunicare agli utenti di disinstallare la versione precedente e installare la nuova versione dalla nuova posizione.

- Includere un `http://www.adatum.com/MyApplication/` aggiornamento che `deploymentProvider` include `http://www.adatum.com/MyApplication/`un che punta a . Quindi, rilasciare un `deploymentProvider` altro aggiornamento `http://subdomain.adatum.com/MyApplication/`in un secondo momento con il punto di .

  Nel secondo esempio si pubblica un'applicazione `deploymentProvider`ClickOnce che specifica e si decide quindi di rimuoverla. Una volta scaricata nei client la nuova versione senza, `deploymentProvider` non è possibile reindirizzare `deploymentProvider` il percorso utilizzato per gli aggiornamenti fino a quando non si rilascia una versione dell'applicazione ripristinata. Come nel primo `deploymentProvider` esempio, deve inizialmente puntare alla posizione di aggiornamento corrente, non alla nuova posizione. In questo caso, se si `deploymentProvider` tenta `http://subdomain.adatum.com/MyApplication/`di inserire un che fa riferimento a , l'aggiornamento successivo non riesce.

## <a name="create-a-deployment"></a>Creare una distribuzione
 Per istruzioni dettagliate sulla creazione di distribuzioni che possono essere distribuite da percorsi di rete diversi, vedere [Procedura dettagliata: distribuire manualmente un'applicazione ClickOnce che non richiede](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)una firma in corso e che mantiene le informazioni di personalizzazione.

## <a name="see-also"></a>Vedere anche
- [*Mage.exe* (strumento per la generazione e la modifica di manifesti)Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (strumento di generazione e modifica di manifesti, client grafico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
