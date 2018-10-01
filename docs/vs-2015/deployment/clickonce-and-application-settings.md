---
title: Impostazioni dell'applicazione e ClickOnce | Microsoft Docs
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
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2aa565721bc934fb78a7b183b0e4b4b637bafaf8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527785"
---
# <a name="clickonce-and-application-settings"></a>Impostazioni dell'applicazione e ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [le impostazioni dell'applicazione e ClickOnce](https://docs.microsoft.com/visualstudio/deployment/clickonce-and-application-settings).  
  
Le impostazioni dell'applicazione per Windows Form semplifica creare, archiviare e gestire applicazioni personalizzate e le preferenze dell'utente nel client. Il documento seguente viene descritto il funzionamento dei file di impostazioni in un'applicazione ClickOnce e modo in cui ClickOnce viene eseguita la migrazione delle impostazioni quando l'utente viene aggiornato alla versione successiva.  
  
 Le informazioni seguenti si applicano solo ai provider di impostazioni dell'applicazione predefinito, il <xref:System.Configuration.LocalFileSettingsProvider> classe. Se si fornisce un provider personalizzato, tale provider determinerà come archiviare i dati e la modalità di aggiornamento delle impostazioni tra le versioni. Per altre informazioni sui provider di impostazioni dell'applicazione, vedere [Application Settings Architecture](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>File delle impostazioni delle applicazioni  
 Le impostazioni dell'applicazione vengono utilizzati due file: *app*. exe. config e User. config, dove *app* è il nome dell'applicazione Windows Form. User. config viene creato nel client la prima volta che l'applicazione archivia le impostazioni con ambito di utente. *app*. exe. config, al contrario, sarà presente prima della distribuzione se si definiscono i valori predefiniti per le impostazioni. Visual Studio includerà questo file automaticamente quando si usa la **pubblica** comando. Se si crea l'applicazione ClickOnce mediante Mage.exe o MageUI.exe, è necessario assicurarsi che questo file è incluso con l'applicazione di altri file quando si popola il manifesto dell'applicazione.  
  
 Nelle applicazioni Windows Form non implementate con ClickOnce, un'applicazione *app*. exe. config è archiviato nella directory dell'applicazione, mentre l'utente è archiviato il file di User. config **Documents and Settings**  cartella. In un'applicazione ClickOnce *app*. exe. config si trova nella directory dell'applicazione all'interno della cache di ClickOnce e User. config si trova nella directory dati per l'applicazione ClickOnce.  
  
 Indipendentemente dal modo in cui si distribuisce l'applicazione, le impostazioni dell'applicazione garantisce sicuro accesso in lettura *app*. exe. config e accesso in lettura/scrittura-safe a User. config.  
  
 In un'applicazione ClickOnce, le dimensioni dei file di configurazione utilizzato dalle impostazioni dell'applicazione sono limitata dalle dimensioni della cache di ClickOnce. Per altre informazioni, vedere [Cenni preliminari sulla Cache di ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Aggiornamenti di versione  
 Esattamente come ogni versione di un'applicazione ClickOnce è isolata da tutte le altre versioni, le impostazioni dell'applicazione per un'applicazione ClickOnce sono isolate fra le impostazioni per anche altre versioni. Quando l'utente viene aggiornato a una versione successiva dell'applicazione, le impostazioni dell'applicazione vengono confrontate le impostazioni più recenti (con numero più alto) della versione con le impostazioni fornite con la versione aggiornata e unisce le impostazioni in un nuovo set di file di impostazioni.  
  
 La tabella seguente descrive come le impostazioni dell'applicazione decide le impostazioni da copiare.  
  
|Tipo di modifica|Azione di aggiornamento|  
|--------------------|--------------------|  
|Impostazione aggiunta a *app*. exe. config|La nuova impostazione viene unita la versione corrente *app*. exe. config|  
|Impostazione rimossi *app*. exe. config|La vecchia impostazione viene rimossa la versione corrente *app*. exe. config|  
|Valore predefinito dell'impostazione modificato. impostazioni locali è ancora impostata sul valore predefinito originale in User. config|L'impostazione viene unita User. config con il nuovo valore predefinito della versione corrente come valore|  
|Valore predefinito dell'impostazione modificato. impostazione impostata su un valore non predefinito in User. config|L'impostazione viene unita di User. config della versione corrente con il valore non predefinito mantenuto|  
  
 Se si hanno creato le proprie impostazioni applicazione classe wrapper e si desidera personalizzare la logica di aggiornamento, è possibile eseguire l'override di <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> (metodo).  
  
## <a name="clickonce-and-roaming-settings"></a>Impostazioni di Roaming e ClickOnce  
 ClickOnce non funziona con le impostazioni di roaming, che consente al file di impostazioni seguire l'utente tra più computer in una rete. Se è necessario che le impostazioni di roaming, è necessario implementare un provider di impostazioni dell'applicazione che archivia le impostazioni di rete o sviluppare le proprie classi di impostazioni personalizzate per archiviare le impostazioni in un computer remoto. Per altre informazioni sul provider di impostazioni, vedere [Application Settings Architecture](http://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Cenni preliminari sulle impostazioni delle applicazioni](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Panoramica della Cache di ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



